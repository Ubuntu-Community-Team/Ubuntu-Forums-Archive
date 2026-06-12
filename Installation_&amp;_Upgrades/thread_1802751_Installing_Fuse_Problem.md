---
title: "Installing Fuse Problem"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by Penchalaiah on 2011-07-12
Hello Friends...

i am using fedora 14 
i getting the following error during ./configure command.

and i tried all combinations like,

1. ./configure
2.  ./configure --enable-kernel-module --with-kernel=/usr/src/kernels/2.6.35.6-45.fc14-i686/
3.   ./configure --enable-kernel-module

all results in following sequence
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... found
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for ranlib... ranlib
checking kernel source directory... /usr/src/kernels/2.6.35.6-45.fc14-i686/
checking kernel source version... Not found
[SIZE=3]**configure: error:**[/SIZE] 
[B]*** Cannot determine the version of the linux kernel source. Please 
*** configure the kernel before running this script[/B]

---

### Post by Penchalaiah on 2011-07-12
> **Penchalaiah said:**
> Hello Friends...

i am using fedora 14 
i getting the following error during ./configure command.

and i tried all combinations like,

1. ./configure
2.  ./configure --enable-kernel-module --with-kernel=/usr/src/kernels/2.6.35.6-45.fc14-i686/
3.   ./configure --enable-kernel-module

all results in following sequence
loading cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... found
checking for working makeinfo... found
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for ranlib... ranlib
checking kernel source directory... /usr/src/kernels/2.6.35.6-45.fc14-i686/
checking kernel source version... Not found
[SIZE=3]**configure: error:**[/SIZE] 
[B]*** Cannot determine the version of the linux kernel source. Please 
*** configure the kernel before running this script[/B]

I am using older version of fuse, so that i am receiving this message...
Now i am using new fuse... no problem at all..

---

