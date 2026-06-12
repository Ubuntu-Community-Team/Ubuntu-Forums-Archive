---
title: "No &quot;makefile&quot; for a Source Package..."
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by GutsyVirgin on 2008-06-13
There have many times I've downloaded a source package that was missing a makefile so I have been unable to compile and "make" and installer for the package. My most recent attempt was with a package called "mms-qt" which I really wanted to use to download mms video streams (or attempt to). The package is missing it's makefile so I have been unable to install. :-k

Is there a way to write my own makefile to install the package? I would really appreciate it if someone could share a detailed tutorial on how to do so for me and others wanting to know the same thing. I have been unable to find an answer to this anywhere. :confused: [FIND THE CONFIGURE RESULTS AND ERROR BELOW]

** Additionally:
If someone knows of an effective way of downloading and saving media streams (mms://...), I would greatly appreciate a tip.

](*,) Cheers!

*****************************************************************
[RUN OF CONFIGURE FILE]:
./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wnon-virtual-dtor... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fexceptions... yes
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -frepo... yes
using lib directory suffix 64
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking for a sed that does not truncate output... 
checking whether ln -s works... yes
checking how to recognise dependant libraries... pass_all
checking for egrep... grep -E
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
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... no
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... no
checking if g++ supports -c -o file.o... no
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
appending configuration tag "GCJ" to libtool
checking if gcj supports -fno-rtti -fno-exceptions... (cached) no
checking for gcj option to produce PIC... -fPIC
checking if gcj PIC flag -fPIC works... no
checking if gcj supports -c -o file.o... no
checking whether the gcj linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking for msgfmt... msgfmt
checking for gmsgfmt... msgfmt
found msgfmt program is not GNU msgfmt; ignore it
checking for xgettext... :
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... socklen_t
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking for poll in -lpoll... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking if res_init is available... yes
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for char... yes
checking size of char... 1
checking for dlopen in -ldl... yes
checking for shl_unload in -ldld... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

[This was run within the proper directory. Note that some files not found.]
[ERROR WHEN ATTEMPTING TO MAKE]:
make
make: *** No targets specified and no makefile found.  Stop.

:confused:

---

### Post by ad_267 on 2008-06-13
There isn't a makefile because the configure script didn't complete properly. 
> checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
The configure script generates the makefile. You need to install the libx11-dev package so that the configure script will run.

---

### Post by GutsyVirgin on 2008-06-13
Thank you for commenting. I still get the same exact error though. Any other suggestions?
-Thanks

---

### Post by ad_267 on 2008-06-13
Try installing the xorg-dev package too and then run ./configure again. There should be an INSTALL file or similar that tells you what dependencies you are most likely to need.

---

### Post by GutsyVirgin on 2008-06-13
Hmmmmmm.... I tried that too, but still the same problem. Anything else you can think of that would be the cause? I just upgraded to Hardy yesterday, but I never had any luck before that either. Would there be any way of creating a makefile myself?

---

### Post by Joeb454 on 2008-06-13
Does it have an autoconf file? Sometimes they don't have makefiles :)

---

### Post by ad_267 on 2008-06-13
The makefile never gets created until the configure script is completed. Once you have installed the dependencies you require the configure script will run without an error and create the makefile. There's no point compiling if you don't have the dependencies you need.

If you are still getting the error "checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!" then maybe you should check with the files you download if there is a list of dependencies required. Because this looks like a qt program maybe you should try installing libqt3-dev and libqt3-headers or libqt4-dev.

---

