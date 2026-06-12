---
title: "[SOLVED] Can't compile source"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by stldirty on 2008-05-14
i'm trying to install awn.  the ./configure works but then when i type make it says "make: *** No targets specified and no makefile found.  Stop."

i have the build-essential package installed.  here's the output for ./configure

[username@username]:~/Desktop/avant-window-navigator-0.2.6$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
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
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
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
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for python... /usr/bin/python
checking for a version of Python >= 2.1.0... yes
checking for a version of Python >= 2.3.5... yes
checking for the distutils Python package... yes
checking for Python include path... -I/usr/include/python2.5
checking for Python library path... -L/usr/lib/python2.5 -lpython2.5
checking for Python site-packages path... ${exec_prefix}/lib/python2.5/site-packages
checking python extra libraries...  -lpthread -ldl  -lutil
checking python extra linking flags... -Xlinker -export-dynamic -Wl,-O1 -Wl,-Bsymbolic-functions
checking consistency of all components of python development environment... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PYGTK... configure: error: Package requirements (gtk+-2.0 pygtk-2.0 >= 2.10.0) were not met:

No package 'gtk+-2.0' found
No package 'pygtk-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYGTK_CFLAGS
and PYGTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by hermes0710 on 2008-05-14
For the first one you need: libgtk2.0-dev
For the second one i think you need: pygtk2-devel (or something like this - it surely needs the dev or devel extention)

---

### Post by stldirty on 2008-05-14
> **hermes0710 said:**
> For the first one you need: libgtk2.0-dev
For the second one i think you need: pygtk2-devel (or something like this - it surely needs the dev or devel extention)
ok the first one worked but i can't find the second one.  maybe the name is slightly off like you said.

---

### Post by Partyboi2 on 2008-05-14
try
```
sudo apt-get install python-gtk2-dev
```If you are using hardy you can install awn from the universe repo

Edit: or follow this guide  [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

---

### Post by stldirty on 2008-05-14
ok i actually finally found a how-to for hardy heron.  the link is [http://itcertforum.com/forum/showthread.php?t=232](http://itcertforum.com/forum/showthread.php?t=232) for future reference.

---

### Post by stldirty on 2008-05-14
> **Partyboi2 said:**
> try
```
sudo apt-get install python-gtk2-dev
```If you are using hardy you can install awn from the universe repo

Edit: or follow this guide  [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

that works too :guitar:

---

