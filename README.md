
# docker-vertcoind

[![Docker Stars](https://img.shields.io/docker/stars/lukechilds/vertcoind.svg)](https://hub.docker.com/r/lukechilds/vertcoind/)
[![Docker Pulls](https://img.shields.io/docker/pulls/lukechilds/vertcoind.svg)](https://hub.docker.com/r/lukechilds/vertcoind/)

> Run a full Vertcoin node with one command

A Docker configuration with sane defaults for running a full
Vertcoin node.

## Usage

```
docker run -v /home/username/vertcoin:/data -p 8333:8333 lukechilds/vertcoind
```

If there is a `vertcoin.conf` in the `/data` volume it will be used. If not, one will be created for you. A secure unique JSON-RPC password will also be generated.

### JSON-RPC

To access JSON-RPC you'll also need to expose port 8332. You probably only want this available to localhost:

```
docker run -v /home/username/vertcoin:/data -p 8333:8333 -p 127.0.0.1:8332:8332 lukechilds/vertcoind
```

### CLI Arguments

All CLI arguments are passed directly through to vertcoind.

You can use this to configure via cli without a config:

```
docker run -v /home/username/vertcoin:/data -p 8333:8333 -p 127.0.0.1:8332:8332 lukechilds/vertcoind -rpcuser=jonsnow -rpcpassword=ikn0wnothin
```

Or just use the container like a vertcoind binary:

```
$ docker run lukechilds/vertcoind -version
Vertcoin Core Daemon version v0.11.1.0-9c5018b
Copyright (C) 2009-2017 The Vertcoin Core developers
Copyright (C) 2009-2017 The Bitcoin Core developers

Please contribute if you find Vertcoin Core useful. Visit
<https://vertcoin.org> for further information about the software.
The source code is available from <https://github.com/vertcoin/vertcoin>.

This is experimental software.
Distributed under the MIT software license, see the accompanying file COPYING
or <https://opensource.org/licenses/MIT>

This product includes software developed by the OpenSSL Project for use in the
OpenSSL Toolkit <https://www.openssl.org> and cryptographic software written by
Eric Young and UPnP software written by Thomas Bernard.
```
