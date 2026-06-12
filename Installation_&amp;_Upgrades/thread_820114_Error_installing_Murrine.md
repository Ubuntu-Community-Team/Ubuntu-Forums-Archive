---
title: "Error installing Murrine"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by Villts on 2008-06-06
I downloaded the murrine, unzipped, used the configure command:

**./configure --prefix=/usr --enable-animation**
[I]checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating murrine.pc
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing depfiles commands
Now run make.[/I]

So I used the "make", then happen an error after, in "sudo make install", or after enter as root, use "make install":

[I]make[1]: Entrando no diretório `/home/vinicius/murrine-0.53.1'
make[1]: Nada a ser feito para `install-exec-am'. = [COLOR="Gray"]in english : nothing to do with "install-exec-am".[/COLOR]
test -z "/usr/lib/gtk-2.0/2.10.0/engines" || /bin/mkdir -p "/usr/lib/gtk-2.0/2.10.0/engines"
 /bin/bash ./libtool --mode=install /usr/bin/install -c  'libmurrine.la' '/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.la'
/usr/bin/install -c .libs/libmurrine.so /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
/usr/bin/install -c .libs/libmurrine.lai /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/gtk-2.0/2.10.0/engines
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/gtk-2.0/2.10.0/engines

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[1]: Saindo do diretório `/home/vinicius/murrine-0.53.1' [COLOR="Gray"]= in english: "quitting directory "home/my user/murrine-0.53.1"[/COLOR]
[/I]

Why does appear this error?

The program not install. =/

Somebody help me, pleeease!!!

---

### Post by Villts on 2008-06-06
I installed gawk and g77... now this happen:

[i]checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... no
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
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 static flag -static works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating murrine.pc
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing depfiles commands
Now run make.[/i]

**make**:

[i]/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1      -g -O2 -MT murrine_rc_style.lo -MD -MP -MF .deps/murrine_rc_style.Tpo -c -o murrine_rc_style.lo `test -f './src/murrine_rc_style.c' || echo './'`./src/murrine_rc_style.c
 gcc -DHAVE_CONFIG_H -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -g -O2 -MT murrine_rc_style.lo -MD -MP -MF .deps/murrine_rc_style.Tpo -c ./src/murrine_rc_style.c -o murrine_rc_style.o
mv -f .deps/murrine_rc_style.Tpo .deps/murrine_rc_style.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1      -g -O2 -MT murrine_style.lo -MD -MP -MF .deps/murrine_style.Tpo -c -o murrine_style.lo `test -f './src/murrine_style.c' || echo './'`./src/murrine_style.c
 gcc -DHAVE_CONFIG_H -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -g -O2 -MT murrine_style.lo -MD -MP -MF .deps/murrine_style.Tpo -c ./src/murrine_style.c -o murrine_style.o
mv -f .deps/murrine_style.Tpo .deps/murrine_style.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1      -g -O2 -MT murrine_theme_main.lo -MD -MP -MF .deps/murrine_theme_main.Tpo -c -o murrine_theme_main.lo `test -f './src/murrine_theme_main.c' || echo './'`./src/murrine_theme_main.c
 gcc -DHAVE_CONFIG_H -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -g -O2 -MT murrine_theme_main.lo -MD -MP -MF .deps/murrine_theme_main.Tpo -c ./src/murrine_theme_main.c -o murrine_theme_main.o
mv -f .deps/murrine_theme_main.Tpo .deps/murrine_theme_main.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1      -g -O2 -MT support.lo -MD -MP -MF .deps/support.Tpo -c -o support.lo `test -f './src/support.c' || echo './'`./src/support.c
 gcc -DHAVE_CONFIG_H -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -g -O2 -MT support.lo -MD -MP -MF .deps/support.Tpo -c ./src/support.c -o support.o
mv -f .deps/support.Tpo .deps/support.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1      -g -O2 -MT animation.lo -MD -MP -MF .deps/animation.Tpo -c -o animation.lo `test -f './src/animation.c' || echo './'`./src/animation.c
 gcc -DHAVE_CONFIG_H -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -g -O2 -MT animation.lo -MD -MP -MF .deps/animation.Tpo -c ./src/animation.c -o animation.o
mv -f .deps/animation.Tpo .deps/animation.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1      -g -O2 -MT murrine_draw.lo -MD -MP -MF .deps/murrine_draw.Tpo -c -o murrine_draw.lo `test -f './src/murrine_draw.c' || echo './'`./src/murrine_draw.c
 gcc -DHAVE_CONFIG_H -I. -I./src -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/pixman-1 -g -O2 -MT murrine_draw.lo -MD -MP -MF .deps/murrine_draw.Tpo -c ./src/murrine_draw.c -o murrine_draw.o
./src/murrine_draw.c: In function 'murrine_draw_frame':
./src/murrine_draw.c:805: warning: passing argument 5 of 'murrine_get_frame_gap_clip' discards qualifiers from pointer target type
mv -f .deps/murrine_draw.Tpo .deps/murrine_draw.Plo
/bin/bash ./libtool --tag=CC   --mode=link gcc  -g -O2 -module -avoid-version -no-undefined  -o libmurrine.la -rpath /usr/lib/gtk-2.0/2.10.0/engines murrine_rc_style.lo murrine_style.lo murrine_theme_main.lo support.lo animation.lo murrine_draw.lo -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0   
mkdir .libs
ar cru .libs/libmurrine.a  murrine_rc_style.o murrine_style.o murrine_theme_main.o support.o animation.o murrine_draw.o
ranlib .libs/libmurrine.a
creating libmurrine.la
(cd .libs && rm -f libmurrine.la && ln -s ../libmurrine.la libmurrine.la)[/i]

**sudo make install**:

[I]make[1]: Entrando no diretório `/home/vinicius/murrine-0.53.1'
make[1]: Nada a ser feito para `install-exec-am'.
test -z "/usr/lib/gtk-2.0/2.10.0/engines" || /bin/mkdir -p "/usr/lib/gtk-2.0/2.10.0/engines"
 /bin/bash ./libtool --mode=install /usr/bin/install -c  'libmurrine.la' '/usr/lib/gtk-2.0/2.10.0/engines/libmurrine.la'
/usr/bin/install -c .libs/libmurrine.lai /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.la
/usr/bin/install -c .libs/libmurrine.a /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.a
chmod 644 /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.a
ranlib /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.a
PATH="$PATH:/sbin" ldconfig -n /usr/lib/gtk-2.0/2.10.0/engines
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib/gtk-2.0/2.10.0/engines

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[1]: Saindo do diretório `/home/vinicius/murrine-0.53.1'[/I]

---

### Post by psyke83 on 2008-06-06
Murrine is already installed in Hardy by default, and available in the repositories for older versions of Ubuntu, I think. If you want the SVN version, you can download Intrepid's version and manually install using dpkg.

If you really want to build from source, the dependencies for the repository's version of Murrine should be sufficient to build the upstream version as well:

```
$ sudo apt-get build-dep gtk2-engines-murrine
```

---

