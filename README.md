Scout Browser (Experimental)
============================

[![Scout Browser Badge](https://img.shields.io/badge/Scout%20Browser-Experimental-orange.svg)](#badge) 

![homepagelogo.png](http://scout.click/userdata/homepagelogo.png)

The Scout Browser is an experimental peer-to-peer Web browser forked from the beaker browser project. It adds new APIs for building hostless applications, using ipfs & our sister search engine. [Visit the Search Engine.](https://scout.click/)

Join us for discussions at #scoutbrowser on Freenode.


## Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Installing](#installing)
  - [Binaries](#binaries)
  - [Building from source](#building-from-source)
- [Documentation](#documentation)
  - [Env Vars](#env-vars)
- [Known issues](#known-issues)
  - [tmux](#tmux)
- [License](#license)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Installing

### Binaries

**Visit the [Releases Page](https://github.com/royhodge/scoutbrowser/releases) to find the installer you need.**

### Building from source

Requires node 6 or higher. On Windows, you may need to use npm version 4, due to a bug in npm 5.

In Linux (and in some cases macOS) you need libtool, m4, and automake:

```bash
sudo apt-get install libtool m4 make g++  # debian/ubuntu
sudo dnf install libtool m4 make gcc-c++  # fedora
```

In Windows, you'll need to install [Python 2.7](https://www.python.org/downloads/release/python-2711/), Visual Studio 2015 or 2017, and [Git](https://git-scm.com/download/win). (You might try [windows-build-tools](https://www.npmjs.com/package/windows-build-tools).) Then run:

```powershell
npm config set python c:/python27
npm config set msvs_version 2015
npm install -g node-gyp
npm install -g gulp
```

To build:

```bash
git clone https://github.com/royhodge/scoutbrowser.git
cd scoutbrowser
npm install
npm run rebuild # see https://github.com/electron/electron/issues/5851
npm start
```

If you pull latest from the repo and get weird module errors, do:

```bash
npm run burnthemall
```

This invokes [the mad king](http://nerdist.com/wp-content/uploads/2016/05/the-mad-king-game-of-thrones.jpg), who will torch your `node_modules/`, and do the full install/rebuild process for you.
`npm start` should work afterwards.

If you're doing development, `npm run watch` to have assets build automatically.

## Documentation

Looking to work on Scout? [Watch this video](https://www.youtube.com/watch?v=YuE9OO-ZDYo) and take a look at [the build notes](./build-notes.md).

- **Web APIs**
  - [DatArchive](https://beakerbrowser.com/docs/apis/dat.html)
  - [Permissions](https://beakerbrowser.com/docs/apis/permissions.html)
  - [Dat.json site manifest](https://beakerbrowser.com/docs/apis/manifest.html)
- **Specs**
  - Implemented
    - [Dat files protocol](https://beakerbrowser.com/docs/inside-beaker/dat-files-protocol.html)
    - [Dat DNS](https://github.com/beakerbrowser/beaker/wiki/Authenticated-Dat-URLs-and-HTTPS-to-Dat-Discovery)
  - Proposed
    - [App Scheme](https://github.com/beakerbrowser/beaker/wiki/App-Scheme)
    - [Installable Web Applications](https://github.com/beakerbrowser/beaker/wiki/Installable-Web-Applications)
    - [Intents](https://github.com/beakerbrowser/beaker/wiki/Intent-Scheme) a URI scheme for composing interactions between apps
    - [Service Discovery](https://github.com/beakerbrowser/beaker/wiki/PSA-Web-Service-Discovery-Protocol)
    - [WebTerm](https://github.com/beakerbrowser/beaker/wiki/WebTerm) a bashlike terminal for Web
- [**Tutorials**](https://beakerbrowser.com/docs/tutorials/)

### Env Vars

- `DEBUG`: which log systems to output? A comma-separated string. Can be `beaker`, `dat`, `bittorrent-dht`, `dns-discovery`, `hypercore-protocol`. Specify `*` for all.
- `BEAKER_OPEN_URL`: open the given URL on load, rather than the previous session or default tab.
- `BEAKER_USER_DATA_PATH`: override the user-data path, therefore changing where data is read/written. Useful for testing. For default value see `userData` in the [electron docs](https://electron.atom.io/docs/api/app/#appgetpathname).
- `BEAKER_DAT_QUOTA_DEFAULT_BYTES_ALLOWED`: override the default max-quota for bytes allowed to be written by a dat site. Useful for testing. Default value is `'500mb'`. This can be a Number or a String. Check [bytes.parse](https://github.com/visionmedia/bytes.js/tree/a4b9af2bf289175f12b3538eb172f2489844b1ec#bytesparsestringnumber-value-numbernull) for supported units and abbreviations.


## Known issues
### tmux

Launching from tmux is known to cause issues with GUI apps in macOS. On Beaker, it may cause the application to hang during startup.

## License

MIT License (MIT)

Copyright (c) 2018 Blue Link Labs

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
