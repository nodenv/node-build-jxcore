# node-build-jxcore

[![Build Status](https://travis-ci.com/nodenv/node-build-jxcore.svg?branch=master)](https://travis-ci.com/nodenv/node-build-jxcore)

node-build-jxcore is an [nodenv][] plugin (or more precisely, a [node-build][] plugin) that provides build definitions for jxcore.

<!-- toc -->

## Installation

### Installing with Homebrew (for OS X users)

Mac OS X users can install node-build-jxcore with the [Homebrew][].
Installing via Homebrew will make node-build aware of jxcore releases automatically.

*This is the recommended method of installation if you installed nodenv or node-build with Homebrew.*

    brew install nodenv/nodenv/node-build-jxcore

### Installing via git-clone

Installing node-build-jxcore as a nodenv plugin will make node-build aware of the jxcore build definitions automatically.

    git clone https://github.com/nodenv/node-build-jxcore.git $(nodenv root)/plugins/node-build-jxcore

This will install node-build-jxcore into the `$(nodenv root)/plugins/node-build-jxcore` directory.
To update node-build-jxcore, run `git pull` to download the latest changes or use [nodenv-update][].

### Installing via npm

Installing via npm is possible, though not the recommended method.
Keep in mind that there is the risk you are installing a nodenv plugin into a node that is itself managed by nodenv.
(It's likely the case you want to be using your `system` node for this.)

    npm install -g @nodenv/node-build-jxcore

After installing, node-build will need to be made aware of the new build definitions.
see [setting node_build_definitions][]

### Installing manually

For precise control over the installation, you can install it manually.

    git clone https://github.com/nodenv/node-build-jxcore.git
    cd node-build-jxcore
    ./install.sh

This will install node-build-jxcore into `/usr/local`.
If you do not have write permission to `/usr/local`, you will need to run `sudo ./install.sh` instead.
You can install to a different prefix by setting the `PREFIX` environment variable.
(Be aware, if you install to a prefix other than that which node-build is installed, you will need to manually set `NODE_BUILD_DEFINITIONS`.)

To update node-build-jxcore after it has been installed, run `git pull` in your cloned copy of the repository, then re-run the install script.
After installing, node-build will need to be made aware of the new build definitions.
see [setting node_build_definitions][]

## Usage

If installed via Homebrew, as a nodenv plugin, or manually using the same `PREFIX` as node-build, then node-build should automatically be aware of the new jxcore build definitions.
Verify by running `nodenv install --list` to see if it includes the release candidate builds. (e.g. 8.0.0-rc.2)

Otherwise, node-build will need to be made aware of the new build definitions manually.

### Setting NODE_BUILD_DEFINITIONS

`NODE_BUILD_DEFINITIONS` is a colon-separated list of paths that include build definitions.

This is done by adding `/path/to/node-build-jxcore/share/node-build` to the `NODE_BUILD_DEFINITIONS` variable.
You can add node-build-jxcore's share path to it in your `.bashrc`:

    export NODE_BUILD_DEFINITIONS=$NODE_BUILD_DEFINITIONS:/path/to/node-build-jxcore/share/node-build

Or add it only when necessary:

    NODE_BUILD_DEFINITIONS=$NODE_BUILD_DEFINITIONS:/path/to/node-build-jxcore/share/node-build nodenv install --list

Either way, you'll need to know the exact location of where node-build-jxcore was installed.
If installed globally via a nodenv-managed npm, it would look something like:
`$(nodenv prefix)/lib/node_modules/@nodenv/node-build-jxcore/share/node-build`.
If installed manually to `PREFIX=/some/path`, it would look something like:
`/some/path/share/node-build`.

### Passing build definition directly

Both `nodenv install` and `node-build` accept a path to a custom definition file in place of a version name.

    nodenv install /path/to/node-build-jxcore/share/node-build/jxcore+sm-0.3.1.1

Or:

    node-build /path/to/node-build-jxcore/share/node-build/jxcore+sm-0.3.1.1 /dest/path/jxcore+sm-0.3.1.1



[homebrew]: http://brew.sh
[nodenv]: https://github.com/nodenv/nodenv
[node-build]: https://github.com/nodenv/node-build
[nodenv-update]: https://github.com/nodenv/nodenv-update
[setting node_build_definitions]: #setting-node_build_definitions
