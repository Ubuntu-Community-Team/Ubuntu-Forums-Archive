---
title: "Help!  An error of installing Tcl"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by gvtheen on 2007-08-13
when  executing  the command "./configure" , I  found the  error hint:

loading cache ./config.cache
checking whether to use symlinks for manpages... no
checking whether to compress the manpages... no
checking whether to add a package name suffix for the manpages... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for building with threads... no (default)
checking if the compiler understands -pipe... yes
checking how to run the C preprocessor... gcc -pipe -E
checking for sin... no
checking for main in -lieee... yes
checking for main in -linet... no
checking for net/errno.h... no
checking for connect... yes
checking for gethostbyname... yes
checking how to build libraries... shared
checking for ranlib... ranlib
checking if 64bit support is requested... no
checking if 64bit Sparc VIS support is requested... no
checking system version (for dynamic loading)...
./configure: 1: Syntax error: Unterminated quoted string


I have no idea what I am supposed to do with the problem!!
Please help me!

---

### Post by stealth17 on 2007-08-15
> **gvtheen said:**
> when  executing  the command "./configure" , I  found the  error hint:

loading cache ./config.cache
checking whether to use symlinks for manpages... no
checking whether to compress the manpages... no
checking whether to add a package name suffix for the manpages... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking for building with threads... no (default)
checking if the compiler understands -pipe... yes
checking how to run the C preprocessor... gcc -pipe -E
checking for sin... no
checking for main in -lieee... yes
checking for main in -linet... no
checking for net/errno.h... no
checking for connect... yes
checking for gethostbyname... yes
checking how to build libraries... shared
checking for ranlib... ranlib
checking if 64bit support is requested... no
checking if 64bit Sparc VIS support is requested... no
checking system version (for dynamic loading)...
./configure: 1: Syntax error: Unterminated quoted string


I have no idea what I am supposed to do with the problem!!
Please help me!

sudo apt-get install tcl8.3

---

### Post by john_gao on 2008-03-17
Dear sir:
   I have the same problem when I complier source navigator, even after I install Tcl8.3
checking system version (for dynamic loading)... ../../../sourcenav-5.2b2/tcl/unix/configure: 1: Syntax error: Unterminated quoted string
configure: error: ../../../sourcenav-5.2b2/tcl/unix/configure failed for unix
configure: error: ../../sourcenav-5.2b2/tcl/configure failed for tcl
Any ideal?
Thanks!

---

### Post by yangcheng on 2008-05-10
> **john_gao said:**
> Dear sir:
   I have the same problem when I complier source navigator, even after I install Tcl8.3
checking system version (for dynamic loading)... ../../../sourcenav-5.2b2/tcl/unix/configure: 1: Syntax error: Unterminated quoted string
configure: error: ../../../sourcenav-5.2b2/tcl/unix/configure failed for unix
configure: error: ../../sourcenav-5.2b2/tcl/configure failed for tcl
Any ideal?
Thanks!

 sudo apt-get install sourcenav

---

