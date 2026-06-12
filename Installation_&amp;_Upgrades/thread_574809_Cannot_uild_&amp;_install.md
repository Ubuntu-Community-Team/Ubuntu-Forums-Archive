---
title: "Cannot uild &amp; install"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by amitabhishek on 2007-10-13
Hi,

I cannot install the packages which needs to be built locally on the system. I always get this error (Example):


amit@amit-desktop:~/Desktop/Apps$ cd /home/amit/Desktop/Apps/anjuta-2.2.1
amit@amit-desktop:~/Desktop/Apps/anjuta-2.2.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.


Pls help. I use Ubuntu 7.04

---

### Post by Pumalite on 2007-10-13
Make sure you have build-essential:

sudo apt-get install build-essential

Then try again.

---

### Post by amitabhishek on 2007-10-13
I did... this is what I got


checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking return type of signal handlers... void
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB... configure: error: Package requirements (glib-2.0 >= 2.8.0) were not met:

No package 'glib-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

amit@amit-desktop:~/Desktop/Apps/anjuta-2.2.1$ /home/amit/Desktop/Apps/anjuta-2.2.1

---

### Post by Pumalite on 2007-10-13
'Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details'

[http://www.linuxheadquarters.com/howto/basic/path.shtml](http://www.linuxheadquarters.com/howto/basic/path.shtml)

---

