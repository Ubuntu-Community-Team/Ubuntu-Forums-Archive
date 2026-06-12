---
title: "Stock installing kpicosim"
date: 2011-11-21
forum: Installation &amp; Upgrades
---

### Post by Peter2009 on 2011-11-21
Hi!

I am trying to installed kpicosim on my Ubuntu 10.04 with kernel 2.6.32-35-generic

I am at the point where I typed:

 ```
make
```

I get:

```
/bin/bash ./config.status --recheck
running /bin/bash ./configure  --without-arts  --no-create --no-recursion
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for g++... g++
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... no
checking whether gcc accepts -g... no
checking for gcc option to accept ISO C89... unsupported
checking dependency style of gcc... gcc3
checking for gcc... (cached) gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... (cached) no
checking whether gcc accepts -g... (cached) no
checking for gcc option to accept ISO C89... (cached) unsupported
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking whether we are using the GNU C++ compiler... (cached) no
checking whether g++ accepts -g... (cached) no
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -O0... yes
checking whether g++ supports -Wl,--no-undefined... yes
checking whether g++ supports -Wl,--allow-shlib-undefined... yes
not using lib directory suffix
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for non-GNU ld... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... gfortran
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether gfortran accepts -g... yes
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking for gcc option to produce PIC... 
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... no
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... 
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) no
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gfortran option to produce PIC... 
checking if gfortran supports -c -o file.o... yes
checking whether the gfortran linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking if C++ programs can be compiled... yes
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... yes
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking sys/bitypes.h usability... yes
checking sys/bitypes.h presence... yes
checking for sys/bitypes.h... yes
checking for poll in -lpoll... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking for res_init... yes
checking if res_init needs custom prototype... no
checking for killpg in -lucb... no
checking size of int... 4
checking size of short... 2
checking size of long... 4
checking size of char *... 4
checking for dlopen in -ldl... (cached) yes
checking for shl_unload in -ldld... no
checking size of size_t... 4
checking size of unsigned long... 4
checking sizeof size_t == sizeof unsigned long... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... libraries /usr/lib, headers .
checking for IceConnectionNumber in -lICE... yes
checking for libXext... yes
checking for pthread_create in -lpthread... yes
checking for extra includes... no
checking for extra libs... no
checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for perl... /usr/bin/perl
checking for Qt... libraries /usr/share/qt3/lib, headers /usr/share/qt3/include using -mt
checking for moc... /usr/share/qt3/bin/moc
checking for uic... /usr/share/qt3/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... libraries /usr/lib, headers /usr/include/kde
checking if UIC has KDE plugins available... yes
checking for KDE paths... defaults
checking for dcopidl... /usr/bin/dcopidl
checking for dcopidl2cpp... /usr/bin/dcopidl2cpp
checking for meinproc... /usr/bin/meinproc
checking for xmllint... /usr/bin/xmllint
checking whether byte ordering is bigendian... no
checking for MAXPATHLEN... 4096
checking if admin should be compiled... no
checking if debian should be compiled... no
checking if doc should be compiled... yes
checking if po should be compiled... yes
checking if src should be compiled... yes
configure: creating ./config.status

Good - your configure finished. Start make now

 /bin/bash ./config.status
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating doc/en/Makefile
config.status: creating po/Makefile
config.status: creating src/Makefile
config.status: creating src/pics/Makefile
config.status: creating config.h
config.status: executing depfiles commands
make  all-recursive
make[1]: Entering directory `/home/ccc/.kpicosim/kpicosim'
Making all in doc
make[2]: Entering directory `/home/ccc/.kpicosim/kpicosim/doc'
make[3]: Entering directory `/home/ccc/.kpicosim/kpicosim/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/ccc/.kpicosim/kpicosim/doc'
make[2]: Leaving directory `/home/ccc/.kpicosim/kpicosim/doc'
Making all in po
make[2]: Entering directory `/home/ccc/.kpicosim/kpicosim/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/ccc/.kpicosim/kpicosim/po'
Making all in src
make[2]: Entering directory `/home/ccc/.kpicosim/kpicosim/src'
Making all in pics
make[3]: Entering directory `/home/ccc/.kpicosim/kpicosim/src/pics'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/ccc/.kpicosim/kpicosim/src/pics'
make[3]: Entering directory `/home/ccc/.kpicosim/kpicosim/src'
g++ -DHAVE_CONFIG_H -I. -I.. -I../debian -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT   -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.cpp
mv -f .deps/main.Tpo .deps/main.Po
g++ -DHAVE_CONFIG_H -I. -I.. -I../debian -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT   -MT kpicosim.o -MD -MP -MF .deps/kpicosim.Tpo -c -o kpicosim.o kpicosim.cpp
kpicosim.cpp:627:24: error: kpicosim.moc: No such file or directory
make[3]: *** [kpicosim.o] Error 1
make[3]: Leaving directory `/home/ccc/.kpicosim/kpicosim/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ccc/.kpicosim/kpicosim/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ccc/.kpicosim/kpicosim'
make: *** [all] Error 2
```

What should I do now?


To get here:

```
had to run: ( and Installed some package and some reading in between)

tar zxvf kpicosim-0.7.tar.gz
sudo apt-get build-dep audacity
aclocal
./configure --without-arts
autoreconf -fi
```

---

