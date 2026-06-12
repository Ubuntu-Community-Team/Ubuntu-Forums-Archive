---
title: "Installation Issues"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by TheFoe92 on 2007-06-19
I am unable to install Danger from the Deep. It has some dependencies, and, while trying to install these, I get stuck on SDL_tff. This too has a dependency: FreeType. This is what I cannot install. After downloading version 2.1.10, I cannot get past the "./configure" part. Here is what it does after typing ./configure:
```
cd builds/unix; ./configure 
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for rm... rm -f
checking for rmdir... rmdir
checking for a BSD-compatible install... /usr/bin/install -c
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for unistd.h... (cached) yes
checking for an ANSI C-conforming const... yes
checking for int... yes
checking size of int... 4
checking for long... yes
checking size of long... 4
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for getpagesize... yes
checking for working mmap... yes
checking whether munmap is declared... yes
checking for munmap's first parameter type... void *
checking for memcpy... yes
checking for memmove... yes
checking for gzsetparams in -lz... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
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
checking for pghpf... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
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
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
configure: creating ./config.status
config.status: creating unix-cc.mk
config.status: creating unix-def.mk
config.status: creating freetype-config
config.status: creating freetype2.pc
config.status: creating ftconfig.h

FreeType build system -- automatic system detection

The following settings are used:

  platform                    unix
  compiler                    cc
  configuration directory     ./builds/unix
  configuration rules         ./builds/unix/unix.mk

If this does not correspond to your system or settings please remove the file
`config.mk' from this directory then read the INSTALL file for help.

Otherwise, simply type `make' again to build the library,
or `make refdoc' to build the API reference (the latter needs python).

make: Nothing to be done for `unix'.

```

I am running Ubuntu Feisty Fawn 7.04. What am I doing wrong? Does this have another dependency? Any suggestions are greatly appreciated. Thanks in advance!

---

### Post by TheFoe92 on 2007-06-25
:( What is wrong? Why is no one answering? Is something missing in the thread? Am I not giving enough information? If you think that this thread is dead, please don't : I am still here in the background, I am just waiting for responses.

---

### Post by rillip on 2007-06-25
I honestly haven't seen a program require this kind of interaction before.

Not to sound dumb, but have you checked all those things are right? I don't have any directories like those.  You may really need to read the install notes as it states... sorry this isn't more helpful, but the best place to get help installing the program would be the provider of the package/source/repository.

---

