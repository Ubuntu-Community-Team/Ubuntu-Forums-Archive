---
title: "GCC toolchain compilation problem"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by adnan.iqbal on 2010-03-12
Hi, 

I have to install crosscompiler for mips. 
System specs:
Ubuntu 9.10, binutil 2.20, 
GCC 4.4.1 source directory : is present in /tmps/gcc-4.4.1
Build directory  : /tmps/build-gcc

I am running ./configure as
 ./configure --prefix=/usr/local --target=mipsel-linux --verbose

after that i run make and get the following error
checking whether to enable maintainer-specific portions of Makefiles... no
checking for mipsel-linux-gcc... /tmp/gcc-build/./gcc/xgcc -B/tmp/gcc-build/./gcc/ -B/usr/local/mipsel-linux/bin/ -B/usr/local/mipsel-linux/lib/ -isystem /usr/local/mipsel-linux/include -isystem /usr/local/mipsel-linux/sys-include
checking for C compiler default output file name... configure: error: in `/tmp/gcc-build/mipsel-linux/libmudflap':
configure: error: C compiler cannot create executables
See `config.log' for more details.
make[1]: *** [configure-target-libmudflap] Error 1
make[1]: Leaving directory `/tmp/gcc-build'
make: *** [all] Error 2

I am really stuck with this problem, Any help shall be greatly appreciated.
Regards
Adnan

---

