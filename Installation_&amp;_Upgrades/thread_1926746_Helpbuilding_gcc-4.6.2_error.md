---
title: "Help:building gcc-4.6.2 error"
date: 2012-02-16
forum: Installation &amp; Upgrades
---

### Post by Derek stallone on 2012-02-16
I chose a gcc 4.6.2. I downloaded gcc-4.6.2.tar.bz2 from here [ftp://ftp.gnu.org/gnu/gcc/gcc-4.4.6/](ftp://ftp.gnu.org/gnu/gcc/gcc-4.4.6/) and made the following steps:
--------------------------------------------------------------------------------------------------
stallone@stallone-desktop:~$mkdir build-gcc
stallone@stallone-desktop:~$cd build-gcc/
stallone@stallone-desktop:~/build-gcc$sudo /usr/src/gcc/gcc-4.6.2/configure --prefix=/usr/gcc-4.6.2/  --with-gmp=/usr/local/gmp --with-mpfr=/usr/src/mpfr --with-mpc=/usr/local/mpc --with-ppl=/usr/local/gmp --with-cloog=/usr/local  LDFLAGS="-L/usr/local/lib -Xlinker -R/usr/local/lib" CONFIG_SHELL=/bin/bash -enable-languages=c,c++,fortran
stallone@stallone-desktop:~/build-gcc$make
----------------------------------------------------------------------------------------------------
And after makeing,I have some errors!
------------------------------------------------------------------------------------------------------
In file included from /usr/src/gcc/gcc-4.6.2/gcc/cp/except.c:912:0:
/usr/src/gcc/gcc-4.6.2/gcc/cp/cfns.gperf:101:1: error: ‘gnu_inline’ attribute present on ‘libc_name_p’
/usr/src/gcc/gcc-4.6.2/gcc/cp/cfns.gperf:26:14: error: but not here
make[3]: *** [cp/except.o] Error 1
make[3]: Leaving directory `/home/stallone/build-gcc/gcc'
make[2]: *** [all-stage2-gcc] Error 2
make[2]: Leaving directory `/home/stallone/build-gcc'
make[1]: *** [stage2-bubble] Error 2
make[1]: Leaving directory `/home/stallone/build-gcc'
make: *** [all] Error 2
--------------------------------------------------------------------------------------------------------
What did I do wrong and how to fix it?

---

