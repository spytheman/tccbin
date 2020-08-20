# thirdparty-linux-arm64

This is a prebuild tcc (git://repo.or.cz/tinycc.git), cut at commit 696b765 .

It is compiled with:
```shell
#!/bin/bash

## should be run in V's main repo folder!

rm -rf tinycc/
rm -rf thirdparty/tcc/

pushd .

git clone git://repo.or.cz/tinycc.git
cd tinycc

./configure --prefix=thirdparty/tcc \
            --bindir=thirdparty/tcc \
            --crtprefix=thirdparty/tcc/lib:/usr/lib64:/usr/lib/aarch64-linux-gnu \
            --libpaths=thirdparty/tcc/lib:/usr/lib/aarch64-linux-gnu:/usr/lib64:/usr/lib:/lib/aarch64-linux-gnu:/lib:/usr/local/lib/aarch64-linux-gnu:/usr/local/lib \
            --debug
make
make install

popd

mv tinycc/thirdparty/tcc thirdparty/tcc

mv thirdparty/tcc/tcc thirdparty/tcc/tcc.exe

thirdparty/tcc/tcc.exe -v -v
```
