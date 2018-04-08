usdkhan Core integration/staging tree
=====================================

[![Build Status](https://travis-ci.org/bitbaba/usdkhan.svg?branch=master)](https://travis-ci.org/bitbaba/usdkhan)

What is usdkhan?
----------------

usdkhan is an new digital gold that enables instant payments to
anyone, anywhere in the world. usdkhan uses peer-to-peer technology to operate
with no central authority: managing transactions and issuing money are carried
out collectively by the network. usdkhan Core is the name of open source
software which enables the use of this currency. see [Features](https://github.com/bitbaba/usdkhan/blob/master/README.md#features)
and [RoadMaps](https://github.com/bitbaba/usdkhan/blob/master/README.md#roadmaps).

For more information, as well as an immediately useable, binary version of
the usdkhan Core software, see https://bintray.bitbaba.com/bintray/usdkhan, or read the
[usdkhan design](http://blog.csdn.net/hacode/article/details/78369398) and
[bitcoin original whitepaper](https://bitcoincore.org/bitcoin.pdf).

Downloads
-------------

- [Win32](https://bintray.bitbaba.com/usdkhan/usdkhan-win32.tar.gz)
- [Ubuntu](https://bintray.bitbaba.com/usdkhan/usdkhan-ubuntu64.tar.gz)
- [Mac](https://bintray.bitbaba.com/usdkhan/usdkhan-mac.tar.gz)
- [minerd](https://bintray.bitbaba.com/usdkhan/usdkhan-miner.zip)

Services
----------------

- [Pool](https://pool.bitbaba.com/)

- [Miner](https://github.com/bitbaba/cpuminer)

- [Explorer](https://usdkhan.bitbaba.com/)

- [Exchange](https://ex.bitbaba.com/)

License
-------

usdkhan Core is released under the terms of the MIT license. 
See [COPYING](COPYING) for more information or see https://opensource.org/licenses/MIT.

Features
--------

- 5 minutes per block(half of bitcoin core)
- 2-Mega-bytes serialized block size(2x bitcoin core)
- 42,000,000 coins in PoW stage(2x of bitcoins and half of litecoins)
- Seg-Witness(same as bitcoin core)
- GoldHash as PoW (now same as sha256d of bitcoin core)

Roadmaps
----------------

- Support chainstate retrieving in script stack machine
  - nonceOf(height) [commits](https://github.com/bitbaba/usdkhan/commits/nonceOf)
  - hashOf(height)
  - timeOf(height)

- Support non-standard sub-script of P2SH

- Support PoS (Proof-of-Stake)

- Support state storage of non-utxo data

Mining 
-------------------
- Pool

```
./minerd --algo=sha256d \
         --threads=1 \
         --url=stratum+tcp://pool.bitbaba.com:3333 \
         --no-getwork \
         --no-gbt \
         --user=GZmKHp12bDUiDCkvvzyZzytwRcNaW3viDM \
         --pass=x \
         --debug \
         --protocol-dump
```

- GBT(GetBlockTemplate) on remote rpc

```
./minerd --algo=sha256d \
	 --threads=1 \
	 --coinbase-sig="bitbaba" \
	 --coinbase-addr=GZmKHp12bDUiDCkvvzyZzytwRcNaW3viDM \
	 --url=http://api.bitbaba.com/ \
	 --no-getwork \
	 --user=rpcuser \
	 --pass=rpcpassword \
	 --debug \
	 --protocol-dump
```

- Solo-Mining Locally

mine.sh

```
while true; 
    do ./usdkhan-cli generatetoaddress 1 GZmKHp12bDUiDCkvvzyZzytwRcNaW3viDM 10000000; 
done
```

mine.bat

```
@echo off
:restart

echo minging...

usdkhan-cli generatetoaddress 1 GZmKHp12bDUiDCkvvzyZzytwRcNaW3viDM 10000000

ping -w 1 -n 5 1.0.0.1

goto :restart
```

>Note: remember to configure usdkhan.conf with:

```
server=1
rpcuser=rpcuser
rpcpassword=rpcpassword
```

Development Process
-------------------

The `master` branch is regularly built and tested, but is not guaranteed to be
completely stable. [Tags](https://github.com/bitbaba/usdkhan/tags) are created
regularly to indicate new official, stable release versions of usdkhan Core.

The contribution workflow is described in [CONTRIBUTING.md](CONTRIBUTING.md).

The developer [mailing list](https://lists.linuxfoundation.org/mailman/listinfo/usdkhan-dev)
should be used to discuss complicated or controversial changes before working
on a patch set.

Developer IRC can be found on Freenode at #usdkhan-core-dev.

Automated Building
------------------

As you known, the .travis.yml is used for automated building. and here is a localized script called *travis.sh*, 
which can be used to build usdkhan on your local laptop.

Example Usage:

```
$>mkdir -p ~/home/user1/tarballs; \
$>ln -s ~/home/user1/tarballs depends/sources; \
$>mkdir -p depends/sdk-sources depends/SDKs; \
$>sudo apt-get update; \
$>sh travis.sh;
```

>Note: *~/home/user1/tarballs* is used to cache locale source tarballs of depends.


