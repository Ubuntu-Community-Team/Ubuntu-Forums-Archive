---
title: "Installing Jahshaka Video Editor"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by KeybladeSephi on 2008-07-17
Hello everyone. I have been searching forever to find a good video editing software (I can't get Cinelerra to install), and I think Jahshaka's my answer. I have downloaded the .run file (is that even the right one?), but when I try to install it, I get this following error, with a string of missing dependencies:

```
keybladesephi@Sheila:~$ cd ~/Desktop
keybladesephi@Sheila:~/Desktop$ chmod +x jahshaka-bundle-2.0FC5.run
keybladesephi@Sheila:~/Desktop$ ./jahshaka-bundle-2.0FC5.run
Creating directory jahshaka-bundle-2.0
Verifying archive integrity... All good.
Uncompressing Jahshaka 2.0 and Jahplayer 0.1.0 Fedora Core 5..........
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Basenames index using db3 - No such file or directory (2)
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Providename index using db3 - No such file or directory (2)
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Conflictname index using db3 - No such file or directory (2)
error: Failed dependencies:
	/usr/bin/env is needed by jahplayer-0.1.0-1.i386
	/sbin/ldconfig is needed by jahshaka-2.0.1-2.i386
	/usr/bin/env is needed by jahshaka-2.0.1-2.i386
	libGL.so.1 is needed by jahshaka-2.0.1-2.i386
	libGLU.so.1 is needed by jahshaka-2.0.1-2.i386
	libSDL-1.2.so.0 is needed by jahshaka-2.0.1-2.i386
	libX11.so.6 is needed by jahshaka-2.0.1-2.i386
	libXext.so.6 is needed by jahshaka-2.0.1-2.i386
	libXi.so.6 is needed by jahshaka-2.0.1-2.i386
	libXmu.so.6 is needed by jahshaka-2.0.1-2.i386
	libboost_filesystem.so.2 is needed by jahshaka-2.0.1-2.i386
	libc.so.6 is needed by jahshaka-2.0.1-2.i386
	libc.so.6(GLIBC_2.0) is needed by jahshaka-2.0.1-2.i386
	libc.so.6(GLIBC_2.1) is needed by jahshaka-2.0.1-2.i386
	libc.so.6(GLIBC_2.1.3) is needed by jahshaka-2.0.1-2.i386
	libc.so.6(GLIBC_2.2) is needed by jahshaka-2.0.1-2.i386
	libc.so.6(GLIBC_2.3) is needed by jahshaka-2.0.1-2.i386
	libc.so.6(GLIBC_2.3.4) is needed by jahshaka-2.0.1-2.i386
	libc.so.6(GLIBC_2.4) is needed by jahshaka-2.0.1-2.i386
	libfreetype.so.6 is needed by jahshaka-2.0.1-2.i386
	libgcc_s.so.1 is needed by jahshaka-2.0.1-2.i386
	libgcc_s.so.1(GCC_3.0) is needed by jahshaka-2.0.1-2.i386
	libgcc_s.so.1(GLIBC_2.0) is needed by jahshaka-2.0.1-2.i386
	libjpeg.so.62 is needed by jahshaka-2.0.1-2.i386
	libm.so.6 is needed by jahshaka-2.0.1-2.i386
	libm.so.6(GLIBC_2.0) is needed by jahshaka-2.0.1-2.i386
	libopenal.so.0 is needed by jahshaka-2.0.1-2.i386
	libpthread.so.0 is needed by jahshaka-2.0.1-2.i386
	libpthread.so.0(GLIBC_2.0) is needed by jahshaka-2.0.1-2.i386
	libpthread.so.0(GLIBC_2.2) is needed by jahshaka-2.0.1-2.i386
	libqt-mt.so.3 is needed by jahshaka-2.0.1-2.i386
	libstdc++.so.6 is needed by jahshaka-2.0.1-2.i386
	libstdc++.so.6(CXXABI_1.3) is needed by jahshaka-2.0.1-2.i386
	libstdc++.so.6(GLIBCXX_3.4) is needed by jahshaka-2.0.1-2.i386
	libz.so.1 is needed by jahshaka-2.0.1-2.i386
	/sbin/ldconfig is needed by jahwidgets-0.1.0-1.i386
	/usr/bin/env is needed by jahwidgets-0.1.0-1.i386
	libGL.so.1 is needed by jahwidgets-0.1.0-1.i386
	libGLU.so.1 is needed by jahwidgets-0.1.0-1.i386
	libX11.so.6 is needed by jahwidgets-0.1.0-1.i386
	libXext.so.6 is needed by jahwidgets-0.1.0-1.i386
	libXmu.so.6 is needed by jahwidgets-0.1.0-1.i386
	libboost_filesystem.so.2 is needed by jahwidgets-0.1.0-1.i386
	libboost_python.so.2 is needed by jahwidgets-0.1.0-1.i386
	libc.so.6 is needed by jahwidgets-0.1.0-1.i386
	libc.so.6(GLIBC_2.0) is needed by jahwidgets-0.1.0-1.i386
	libc.so.6(GLIBC_2.1.3) is needed by jahwidgets-0.1.0-1.i386
	libgcc_s.so.1 is needed by jahwidgets-0.1.0-1.i386
	libgcc_s.so.1(GCC_3.0) is needed by jahwidgets-0.1.0-1.i386
	libm.so.6 is needed by jahwidgets-0.1.0-1.i386
	libm.so.6(GLIBC_2.0) is needed by jahwidgets-0.1.0-1.i386
	libpthread.so.0 is needed by jahwidgets-0.1.0-1.i386
	libqt-mt.so.3 is needed by jahwidgets-0.1.0-1.i386
	libqui.so.1 is needed by jahwidgets-0.1.0-1.i386
	libstdc++.so.6 is needed by jahwidgets-0.1.0-1.i386
	libstdc++.so.6(CXXABI_1.3) is needed by jahwidgets-0.1.0-1.i386
	libstdc++.so.6(GLIBCXX_3.4) is needed by jahwidgets-0.1.0-1.i386
	python(abi) = 2.4 is needed by jahwidgets-0.1.0-1.i386
	/bin/sh is needed by olib-glew-1.3.4-4.i386
	/sbin/ldconfig is needed by olib-glew-1.3.4-4.i386
	libGL.so.1 is needed by olib-glew-1.3.4-4.i386
	libGLU.so.1 is needed by olib-glew-1.3.4-4.i386
	libX11.so.6 is needed by olib-glew-1.3.4-4.i386
	libXext.so.6 is needed by olib-glew-1.3.4-4.i386
	libXi.so.6 is needed by olib-glew-1.3.4-4.i386
	libXmu.so.6 is needed by olib-glew-1.3.4-4.i386
	libc.so.6 is needed by olib-glew-1.3.4-4.i386
	libc.so.6(GLIBC_2.0) is needed by olib-glew-1.3.4-4.i386
	libc.so.6(GLIBC_2.1) is needed by olib-glew-1.3.4-4.i386
	/sbin/ldconfig is needed by olib-mlt++-0.2.2-1.i386
	libc.so.6 is needed by olib-mlt++-0.2.2-1.i386
	libc.so.6(GLIBC_2.0) is needed by olib-mlt++-0.2.2-1.i386
	libc.so.6(GLIBC_2.1) is needed by olib-mlt++-0.2.2-1.i386
	libc.so.6(GLIBC_2.1.3) is needed by olib-mlt++-0.2.2-1.i386
	libgcc_s.so.1 is needed by olib-mlt++-0.2.2-1.i386
	libgcc_s.so.1(GCC_3.0) is needed by olib-mlt++-0.2.2-1.i386
	libm.so.6 is needed by olib-mlt++-0.2.2-1.i386
	libstdc++.so.6 is needed by olib-mlt++-0.2.2-1.i386
	libstdc++.so.6(CXXABI_1.3) is needed by olib-mlt++-0.2.2-1.i386
	libstdc++.so.6(GLIBCXX_3.4) is needed by olib-mlt++-0.2.2-1.i386
	/sbin/ldconfig is needed by olib-mlt-0.2.2-1.i386
	libSDL-1.2.so.0 is needed by olib-mlt-0.2.2-1.i386
	libatk-1.0.so.0 is needed by olib-mlt-0.2.2-1.i386
	libavcodec.so.51 is needed by olib-mlt-0.2.2-1.i386
	libavformat.so.50 is needed by olib-mlt-0.2.2-1.i386
	libavutil.so.49 is needed by olib-mlt-0.2.2-1.i386
	libc.so.6 is needed by olib-mlt-0.2.2-1.i386
	libc.so.6(GLIBC_2.0) is needed by olib-mlt-0.2.2-1.i386
	libc.so.6(GLIBC_2.1) is needed by olib-mlt-0.2.2-1.i386
	libc.so.6(GLIBC_2.1.3) is needed by olib-mlt-0.2.2-1.i386
	libc.so.6(GLIBC_2.2) is needed by olib-mlt-0.2.2-1.i386
	libc.so.6(GLIBC_2.2.3) is needed by olib-mlt-0.2.2-1.i386
	libc.so.6(GLIBC_2.3) is needed by olib-mlt-0.2.2-1.i386
	libcairo.so.2 is needed by olib-mlt-0.2.2-1.i386
	libdl.so.2 is needed by olib-mlt-0.2.2-1.i386
	libdl.so.2(GLIBC_2.0) is needed by olib-mlt-0.2.2-1.i386
	libdl.so.2(GLIBC_2.1) is needed by olib-mlt-0.2.2-1.i386
	libgcc_s.so.1 is needed by olib-mlt-0.2.2-1.i386
	libgcc_s.so.1(GCC_3.0) is needed by olib-mlt-0.2.2-1.i386
	libgdk-x11-2.0.so.0 is needed by olib-mlt-0.2.2-1.i386
	libgdk_pixbuf-2.0.so.0 is needed by olib-mlt-0.2.2-1.i386
	libglib-2.0.so.0 is needed by olib-mlt-0.2.2-1.i386
	libgmodule-2.0.so.0 is needed by olib-mlt-0.2.2-1.i386
	libgobject-2.0.so.0 is needed by olib-mlt-0.2.2-1.i386
	libgtk-x11-2.0.so.0 is needed by olib-mlt-0.2.2-1.i386
	libm.so.6 is needed by olib-mlt-0.2.2-1.i386
	libpango-1.0.so.0 is needed by olib-mlt-0.2.2-1.i386
	libpangocairo-1.0.so.0 is needed by olib-mlt-0.2.2-1.i386
	libpangoft2-1.0.so.0 is needed by olib-mlt-0.2.2-1.i386
	libpthread.so.0 is needed by olib-mlt-0.2.2-1.i386
	libpthread.so.0(GLIBC_2.0) is needed by olib-mlt-0.2.2-1.i386
	libpthread.so.0(GLIBC_2.1) is needed by olib-mlt-0.2.2-1.i386
	libpthread.so.0(GLIBC_2.3.2) is needed by olib-mlt-0.2.2-1.i386
	libstdc++.so.6 is needed by olib-mlt-0.2.2-1.i386
	libstdc++.so.6(CXXABI_1.3) is needed by olib-mlt-0.2.2-1.i386
	libstdc++.so.6(GLIBCXX_3.4) is needed by olib-mlt-0.2.2-1.i386
	libvorbis.so.0 is needed by olib-mlt-0.2.2-1.i386
	libvorbisfile.so.3 is needed by olib-mlt-0.2.2-1.i386
	libxml2.so.2 is needed by olib-mlt-0.2.2-1.i386
	libz.so.1 is needed by olib-mlt-0.2.2-1.i386
	/bin/sh is needed by openlibraries-0.3.0-4.i386
	ld-linux.so.2 is needed by openlibraries-0.3.0-4.i386
	ld-linux.so.2(GLIBC_2.3) is needed by openlibraries-0.3.0-4.i386
	libGL.so.1 is needed by openlibraries-0.3.0-4.i386
	libGLU.so.1 is needed by openlibraries-0.3.0-4.i386
	libHalf.so.2 is needed by openlibraries-0.3.0-4.i386
	libIex.so.2 is needed by openlibraries-0.3.0-4.i386
	libIlmImf.so.2 is needed by openlibraries-0.3.0-4.i386
	libImath.so.2 is needed by openlibraries-0.3.0-4.i386
	libavcodec.so.51 is needed by openlibraries-0.3.0-4.i386
	libavformat.so.50 is needed by openlibraries-0.3.0-4.i386
	libavutil.so.49 is needed by openlibraries-0.3.0-4.i386
	libboost_filesystem.so.2 is needed by openlibraries-0.3.0-4.i386
	libboost_python.so.2 is needed by openlibraries-0.3.0-4.i386
	libboost_regex.so.2 is needed by openlibraries-0.3.0-4.i386
	libboost_thread.so.2 is needed by openlibraries-0.3.0-4.i386
	libc.so.6 is needed by openlibraries-0.3.0-4.i386
	libc.so.6(GLIBC_2.0) is needed by openlibraries-0.3.0-4.i386
	libc.so.6(GLIBC_2.1) is needed by openlibraries-0.3.0-4.i386
	libc.so.6(GLIBC_2.1.3) is needed by openlibraries-0.3.0-4.i386
	libc.so.6(GLIBC_2.4) is needed by openlibraries-0.3.0-4.i386
	libgcc_s.so.1 is needed by openlibraries-0.3.0-4.i386
	libgcc_s.so.1(GCC_3.0) is needed by openlibraries-0.3.0-4.i386
	libgcc_s.so.1(GCC_3.3) is needed by openlibraries-0.3.0-4.i386
	libgcc_s.so.1(GCC_4.2.0) is needed by openlibraries-0.3.0-4.i386
	libgcc_s.so.1(GLIBC_2.0) is needed by openlibraries-0.3.0-4.i386
	libglut.so.3 is needed by openlibraries-0.3.0-4.i386
	libjpeg.so.62 is needed by openlibraries-0.3.0-4.i386
	libm.so.6 is needed by openlibraries-0.3.0-4.i386
	libm.so.6(GLIBC_2.0) is needed by openlibraries-0.3.0-4.i386
	libopenal.so.0 is needed by openlibraries-0.3.0-4.i386
	libpng12.so.0 is needed by openlibraries-0.3.0-4.i386
	libpthread.so.0 is needed by openlibraries-0.3.0-4.i386
	libpthread.so.0(GLIBC_2.0) is needed by openlibraries-0.3.0-4.i386
	libqt-mt.so.3 is needed by openlibraries-0.3.0-4.i386
	libsqlite3.so.0 is needed by openlibraries-0.3.0-4.i386
	libstdc++.so.6 is needed by openlibraries-0.3.0-4.i386
	libstdc++.so.6(CXXABI_1.3) is needed by openlibraries-0.3.0-4.i386
	libstdc++.so.6(GLIBCXX_3.4) is needed by openlibraries-0.3.0-4.i386
	libtiff.so.3 is needed by openlibraries-0.3.0-4.i386
	libxml2.so.2 is needed by openlibraries-0.3.0-4.i386
	libz.so.1 is needed by openlibraries-0.3.0-4.i386
```

How do I fix this problem and install Jahshaka?

---

### Post by Partyboi2 on 2008-07-18
Looks like that is for fedora core.
Maybe [[COLOR=Blue]this[/COLOR]]("http://repo.jahshaka.org/ubuntu/dapper/binary-i386/") deb will work

---

### Post by KeybladeSephi on 2008-07-18
Ah, thank you very much (again), Partyboi2 =]. However, I still have an unsatisfied dependency. The error from the package installer is as follows:

```
Package: jahshaka
Error: Dependency is not satisfiable: openlibraries
```

How to I get openlibraries?

---

### Post by KeybladeSephi on 2008-07-18
Also, for the jahplayer deb package, I get another unstatisfied dependency: jahwidgets. Does that come with Jahshaka?

---

### Post by Partyboi2 on 2008-07-19
I had a search around and found that if your are using gusty or hardy you will need to compile the program to get it to work.

---

### Post by KeybladeSephi on 2008-07-19
I am running Hardy; how exactly do you compile Jahshaka?

---

### Post by Partyboi2 on 2008-07-19
I played around with it the other day and so far have been unsuccessful at compiling the openlibraries that is required for it. 
You will need the jahshaka source ([http://downloads.sourceforge.net/jahshakafx/jahshaka.tar.gz?modtime=1160043850&big_mirror=1](http://downloads.sourceforge.net/jahshakafx/jahshaka.tar.gz?modtime=1160043850&big_mirror=1))
and openlibraries ([http://downloads.sourceforge.net/openlibraries/openlibraries-0.4.0.tar.gz?modtime=1177088886&big_mirror=0](http://downloads.sourceforge.net/openlibraries/openlibraries-0.4.0.tar.gz?modtime=1177088886&big_mirror=0))

I have not read of any that have successfully installed it on hardy. So if you manage to get it installed please let me know.

A few links that might help
[http://jahshaka.org/forum/guide-compile-ubuntu-gutsy-amd64-t1604.html](http://jahshaka.org/forum/guide-compile-ubuntu-gutsy-amd64-t1604.html)
[http://209.85.171.104/translate_c?hl=en&sl=fr&u=http://jahshaka.org/wiki/index.php/Deprecated_Hackers_Guide&prev=/search%3Fq%3Dlibopenobjectlib%2Bubuntu%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:unofficial%26hs%3DJ8%26sa%3DG&usg=ALkJrhhDwys4dJ3mkVpBtXrAQGfSskenDw](http://209.85.171.104/translate_c?hl=en&sl=fr&u=http://jahshaka.org/wiki/index.php/Deprecated_Hackers_Guide&prev=/search%3Fq%3Dlibopenobjectlib%2Bubuntu%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:unofficial%26hs%3DJ8%26sa%3DG&usg=ALkJrhhDwys4dJ3mkVpBtXrAQGfSskenDw)
[http://openlibraries.org/wiki/BuildingUbuntuEight](http://openlibraries.org/wiki/BuildingUbuntuEight)

---

### Post by KeybladeSephi on 2008-07-20
Thank you so much, Partyboi2. I am trying to compile openlibraries and am still unsuccussful.

---

### Post by KeybladeSephi on 2008-07-20
When I ran ./configure from the path of openlibraries, I got this:

```
keybladesephi@Sheila:~$ cd ~/Desktop/openlibraries-0.4.0
keybladesephi@Sheila:~/Desktop/openlibraries-0.4.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking whether make sets $(MAKE)... (cached) yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognise dependent libraries... pass_all
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
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for dlopen in -ldl... (cached) yes
checking if compiler is 64bit... lib
checking for sin in -lm... yes
checking for uncompress in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for BZ2_bzDecompress in -lbz2... yes
checking bzlib.h usability... yes
checking bzlib.h presence... yes
checking for bzlib.h... yes
checking for sqlite3_exec in -lsqlite3... yes
checking sqlite3.h usability... yes
checking sqlite3.h presence... yes
checking for sqlite3.h... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking the OpenGL environment... checking for glPushMatrix in -lGL... yes
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking for gluPerspective in -lGLU... yes
checking GL/glu.h usability... yes
checking GL/glu.h presence... yes
checking for GL/glu.h... yes
checking for glutInit in -lglut... yes
checking GL/glut.h usability... yes
checking GL/glut.h presence... yes
checking for GL/glut.h... yes
*** GLEW prefix is not defined. Will use system defaults. ***
checking for glewInit in -lGLEW... yes
checking GL/glew.h usability... yes
checking GL/glew.h presence... yes
checking for GL/glew.h... yes
checking for cgCreateProgramFromFile in -lCg... no
configure: WARNING: *** NVIDIA Cg runtime is not available. All Cg dependent parts will be disabled ***
checking for GelatoAPI::CreateRenderer in -lgelato... no
configure: WARNING: *** NVIDIA Gelato(tm) runtime is not available. All Gelato(tm) dependent parts will be disabled ***
configure: WARNING: *** Boost version is not defined. Will use system defaults. ***
configure: WARNING: *** Boost toolset is not defined. Will use system defaults. ***
configure: WARNING: *** Boost runtime is not defined. Will use system defaults. ***
configure: WARNING: *** Boost thread runtime is not defined. Will use system defaults. ***
checking boost/shared_ptr.hpp usability... yes
checking boost/shared_ptr.hpp presence... yes
checking for boost/shared_ptr.hpp... yes
checking boost/filesystem/fstream.hpp usability... yes
checking boost/filesystem/fstream.hpp presence... yes
checking for boost/filesystem/fstream.hpp... yes
checking for xml2-config... /usr/bin/xml2-config
configure: *** Configuring OpenImageLib ***
checking for libpng-config... /usr/bin/libpng-config
checking for jpeg_read_header in -ljpeg... yes
checking for TIFFOpen in -ltiff... yes
checking the availability of Apple's QuickTime SDK... no
checking for pkg-config... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBAVFORMAT... yes
checking for caca-config... /usr/bin/caca-config
checking for mlt-config... /usr/bin/mlt-config
checking for sdl-config... /usr/bin/sdl-config
checking for QApplication in -lqt-mt... yes
checking qapplication.h usability... yes
checking qapplication.h presence... yes
checking for qapplication.h... yes
checking for OPENEXR... yes
*** OpenAL prefix is not defined. Will use system defaults. ***
checking for alEnable in -lopenal... yes
checking AL/al.h usability... yes
checking AL/al.h presence... yes
checking for AL/al.h... yes
checking /usr/include/python2.4/Python.h usability... yes
checking /usr/include/python2.4/Python.h presence... yes
checking for /usr/include/python2.4/Python.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/openpluginlib/Makefile
config.status: creating src/openpluginlib/pl/Makefile
config.status: creating src/openpluginlib/py/Makefile
config.status: creating src/openimagelib/Makefile
config.status: creating src/openimagelib/il/Makefile
config.status: creating src/openimagelib/plugins/Makefile
config.status: creating src/openimagelib/plugins/3D_lightmap/Makefile
config.status: creating src/openimagelib/plugins/dds/Makefile
config.status: creating src/openimagelib/plugins/dpx/Makefile
config.status: creating src/openimagelib/plugins/exr/Makefile
config.status: creating src/openimagelib/plugins/hdr/Makefile
config.status: creating src/openimagelib/plugins/jpg/Makefile
config.status: creating src/openimagelib/plugins/png/Makefile
config.status: creating src/openimagelib/plugins/qim/Makefile
config.status: creating src/openimagelib/plugins/quicktime/Makefile
config.status: creating src/openimagelib/plugins/sgi/Makefile
config.status: creating src/openimagelib/plugins/tga/Makefile
config.status: creating src/openimagelib/plugins/tiff/Makefile
config.status: creating src/openimagelib/py/Makefile
config.status: creating src/openmedialib/Makefile
config.status: creating src/openmedialib/ml/Makefile
config.status: creating src/openmedialib/plugins/Makefile
config.status: creating src/openmedialib/plugins/template/Makefile
config.status: creating src/openmedialib/plugins/avformat/Makefile
config.status: creating src/openmedialib/plugins/oil/Makefile
config.status: creating src/openmedialib/plugins/caca/Makefile
config.status: creating src/openmedialib/plugins/glew/Makefile
config.status: creating src/openmedialib/plugins/openal/Makefile
config.status: creating src/openmedialib/plugins/mlt/Makefile
config.status: creating src/openmedialib/plugins/sdl/Makefile
config.status: creating src/openmedialib/plugins/gensys/Makefile
config.status: creating src/openmedialib/plugins/quicktime/Makefile
config.status: creating src/openmedialib/py/Makefile
config.status: creating src/openobjectlib/Makefile
config.status: creating src/openobjectlib/sg/Makefile
config.status: creating src/openobjectlib/plugins/Makefile
config.status: creating src/openobjectlib/plugins/3ds/Makefile
config.status: creating src/openobjectlib/plugins/Collada/Makefile
config.status: creating src/openobjectlib/plugins/Gelato/Makefile
config.status: creating src/openobjectlib/plugins/Gelato/gelato/Makefile
config.status: creating src/openobjectlib/plugins/Gelato/gelato_x3d/Makefile
config.status: creating src/openobjectlib/plugins/obj/Makefile
config.status: creating src/openobjectlib/plugins/tsto/Makefile
config.status: creating src/openobjectlib/plugins/X3D/Makefile
config.status: creating src/openobjectlib/plugins/x3dbz/Makefile
config.status: creating src/openobjectlib/plugins/x3dz/Makefile
config.status: creating src/openassetlib/Makefile
config.status: creating src/openassetlib/al/Makefile
config.status: creating src/openassetlib/py/Makefile
config.status: creating src/openassetlib/plugins/Makefile
config.status: creating src/openassetlib/plugins/filesystem_storage_plugin/Makefile
config.status: creating src/openassetlib/plugins/sqlite3_metadata_plugin/Makefile
config.status: creating src/openeffectslib/Makefile
config.status: creating src/openeffectslib/fx/Makefile
config.status: creating src/openeffectslib/plugins/Makefile
config.status: creating src/openeffectslib/plugins/colour_effect/Makefile
config.status: creating src/openeffectslib/plugins/gpu_kernel/Makefile
config.status: creating src/openeffectslib/plugins/openimagelib_source/Makefile
config.status: creating src/openeffectslib/plugins/openmedialib_source/Makefile
config.status: creating media/Makefile
config.status: creating effects/Makefile
config.status: creating test/Makefile
config.status: creating test/openpluginlib/Makefile
config.status: creating test/openpluginlib/discovery/Makefile
config.status: creating test/openpluginlib/enumerate/Makefile
config.status: creating test/openpluginlib/gettimeofday/Makefile
config.status: creating test/openpluginlib/gpu_timer_query/Makefile
config.status: creating test/openpluginlib/initialization/Makefile
config.status: creating test/openpluginlib/rdtsc/Makefile
config.status: creating test/openpluginlib/pcos/Makefile
config.status: creating test/openpluginlib/pcos/key/Makefile
config.status: creating test/openpluginlib/pcos/property/Makefile
config.status: creating test/openpluginlib/pcos/subject-observer/Makefile
config.status: creating test/openpluginlib/pcos/property_container/Makefile
config.status: creating test/openimagelib/Makefile
config.status: creating test/openimagelib/GL/Makefile
config.status: creating test/openimagelib/GL/_2D/Makefile
config.status: creating test/openimagelib/GL/_2D_compressed/Makefile
config.status: creating test/openimagelib/GL/_2D_compressed_cubemap/Makefile
config.status: creating test/openimagelib/GL/_2D_crop/Makefile
config.status: creating test/openimagelib/GL/_2D_crop2/Makefile
config.status: creating test/openimagelib/GL/_2D_exr/Makefile
config.status: creating test/openimagelib/GL/_2D_photoshop/Makefile
config.status: creating test/openimagelib/GL/_2D_scale/Makefile
config.status: creating test/openimagelib/GL/_2D_sgi/Makefile
config.status: creating test/openimagelib/Serialization/Makefile
config.status: creating test/openimagelib/Serialization/png_storer/Makefile
config.status: creating test/openmedialib/Makefile
config.status: creating test/openmedialib/player/Makefile
config.status: creating test/openmedialib/store/Makefile
config.status: creating test/openobjectlib/Makefile
config.status: creating test/openobjectlib/Gelato/Makefile
config.status: creating test/openobjectlib/Gelato/plastic_shader_draw/Makefile
config.status: creating test/openobjectlib/GL/Makefile
config.status: creating test/openobjectlib/GL/Cg_draw/Makefile
config.status: creating test/openobjectlib/GL/CgFX_draw/Makefile
config.status: creating test/openobjectlib/GL/Collada_simple_draw/Makefile
config.status: creating test/openobjectlib/GL/fixed_function_dot_product3_draw/Makefile
config.status: creating test/openobjectlib/GL/fixed_function_multi_texture_draw/Makefile
config.status: creating test/openobjectlib/GL/fixed_function_texture_draw/Makefile
config.status: creating test/openobjectlib/GL/multipass_draw/Makefile
config.status: creating test/openobjectlib/GL/noise_volume/Makefile
config.status: creating test/openobjectlib/GL/obj_draw/Makefile
config.status: creating test/openobjectlib/GL/simple_draw/Makefile
config.status: creating test/openobjectlib/GL/texture_draw/Makefile
config.status: creating test/openobjectlib/Misc/Makefile
config.status: creating test/openobjectlib/Misc/simple/Makefile
config.status: creating test/openobjectlib/Serialization/Makefile
config.status: creating test/openobjectlib/Serialization/importer/Makefile
config.status: creating test/openassetlib/Makefile
config.status: creating test/openassetlib/al_testharness/Makefile
config.status: creating test/openeffectslib/Makefile
config.status: creating test/openeffectslib/GL/Makefile
config.status: creating test/openeffectslib/GL/fbo_render_to_texture/Makefile
config.status: creating test/openeffectslib/GL/network_evaluator/Makefile
config.status: creating test/openeffectslib/GL/still_image_source/Makefile
config.status: creating test/openeffectslib/Misc/Makefile
config.status: creating test/openeffectslib/Misc/enumerate_parameters/Makefile
config.status: creating openlibraries.pc
config.status: creating openlibraries_global_config.hpp
config.status: openlibraries_global_config.hpp is unchanged
config.status: executing depfiles commands
```

About halfway down when It's configuring Nvidia, it gives me this warning:

```
configure: WARNING: *** NVIDIA Cg runtime is not available. All Cg dependent parts will be disabled ***
checking for GelatoAPI::CreateRenderer in -lgelato... no
configure: WARNING: *** NVIDIA Gelato(tm) runtime is not available. All Gelato(tm) dependent parts will be disabled ***
configure: WARNING: *** Boost version is not defined. Will use system defaults. ***
configure: WARNING: *** Boost toolset is not defined. Will use system defaults. ***
configure: WARNING: *** Boost runtime is not defined. Will use system defaults. ***
configure: WARNING: *** Boost thread runtime is not defined. Will use system defaults. ***
```

When I ran make, this is the error I got this error at the end:

```

make[5]: *** [libopenmedialib_avformat_la-avformat_plugin.lo] Error 1
make[5]: Leaving directory `/home/keybladesephi/Desktop/openlibraries-0.4.0/src/openmedialib/plugins/avformat'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/keybladesephi/Desktop/openlibraries-0.4.0/src/openmedialib/plugins'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/keybladesephi/Desktop/openlibraries-0.4.0/src/openmedialib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/keybladesephi/Desktop/openlibraries-0.4.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/keybladesephi/Desktop/openlibraries-0.4.0'
make: *** [all] Error 2
```

When I ran sudo make install, I got similar errors from when I ran make:

```
make[4]: *** [libopenmedialib_avformat_la-avformat_plugin.lo] Error 1
make[4]: Leaving directory `/home/keybladesephi/Desktop/openlibraries-0.4.0/src/openmedialib/plugins/avformat'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/keybladesephi/Desktop/openlibraries-0.4.0/src/openmedialib/plugins'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/keybladesephi/Desktop/openlibraries-0.4.0/src/openmedialib'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/keybladesephi/Desktop/openlibraries-0.4.0/src'
make: *** [install-recursive] Error 1
```

Do you think I'm missing anything else that could cause these errors?

---

### Post by Partyboi2 on 2008-07-21
> make[4]: *** [libopenmedialib_avformat_la-avformat_plugin.lo] Error 1  Unfortunately this is as far as I have got.

---

### Post by KeybladeSephi on 2008-07-21
Ah, you've gotten farther than me =\; please don't give up ='[. Thank you so much =D

---

### Post by Tigin on 2008-07-21
Hello i dont want to be pessimistic and no offence, but the video editors that ubuntu support do not even staisfy a little bright high school student ,  this is one of the weak points of Ubuntu  .

I had to use another distro on my desktop to run cinerella , cinepaint , raw theraphy etc. together .

---

### Post by Partyboi2 on 2008-07-22
To install openlibraries you can add this repo to your  3rd party software in Software Sources
> deb [http://ppa.launchpad.net/rexbron/ubuntu](http://ppa.launchpad.net/rexbron/ubuntu) hardy mainthen install the openlibraries packages
libopenlibraries0
libopenlibraries-dev
openlibraries-common
python-openlibraries
then you can move onto compiling jahshaka, but I got stuck again and think its probably better to wait for the developers to release jahshaka3 sometime hopefully in the near future and that it will be more friendly towards debian based linux.
Another way you can run jahshaka in the meantime is using wine. If you have not already done so install wine
```
sudo apt-get install wine
``` then download the windows version of jahshaka from [[COLOR=Blue]here[/COLOR]]("http://downloads.sourceforge.net/jahshakafx/jahshaka-2.0-installer.exe?modtime=1159912970&big_mirror=1") and install it in wine.

---

### Post by KeybladeSephi on 2008-07-22
Ah yeah I was thinking of using Wine to run the Windows version. However, I don't quite get how to add the "repo"  to my 3rd party software. Could you tell me how to do that?

---

### Post by Partyboi2 on 2008-07-22
Open up Software Sources (System>Admin>Software Sources) on the 2nd tab (3rd party software) click on "add" then in the window that opens add 
```
deb [http://ppa.launchpad.net/rexbron/ubuntu hardy main]("http://ppa.launchpad.net/rexbron/ubuntu")
``` then "add source" then close Software Sources allowing it to reload.
Another way is from the terminal
```
sudo echo deb http://ppa.launchpad.net/rexbron/ubuntu hardy main | sudo tee -a /etc/apt/sources.list
```then
```
sudo apt-get update
```

---

### Post by KeybladeSephi on 2008-07-23
I have installed it on Wine, but for some reason, It won't open when I click it. I get no error or anything; it just doesn't open...

---

### Post by Partyboi2 on 2008-07-23
cd to where the  jahshaka-2.0-installer.exe file is and try
```
 wine jahshaka-2.0-installer.exe 
``` and see what the output in the terminal is.

---

### Post by KeybladeSephi on 2008-07-23
Ah still doesn't work. I'll just wait until the stable version comes out

---

### Post by mateuszbaranski on 2008-10-21
> **KeybladeSephi said:**
> Ah still doesn't work. I'll just wait until the stable version comes out

in my installation of hardy it almost works in wine BUT the diplay is messed up - the whole program works (menus etc.) but playing anything does not - the animation is deformed

---

