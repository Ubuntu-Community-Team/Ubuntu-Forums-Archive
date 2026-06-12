---
title: "Can't install Dreamchess (No makefile found)"
date: 2014-08-07
forum: Installation &amp; Upgrades
---

### Post by stretch4 on 2014-08-07
Trying to install dreamchess, and it's giving me a couple errors. Take a look:

```

stretch@Lappy-X:~/Desktop/dreamchess-0.2.0$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for ranlib... ranlib
checking for flex... no
checking for lex... no
checking for bison... no
checking for inline... inline
checking for ISO C99 varargs macros... yes
checking for GNU C varargs macros... yes
checking for sdl-config... no
checking for SDL - version >= 1.2.6... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
checking for SDL_image.h... no
checking for SDL_opengl.h... no
checking for sqrt in -lm... yes
checking for compress in -lz... no
checking for png_create_read_struct in -lpng... no
checking for jpeg_CreateCompress in -ljpeg... no
checking for IMG_LoadPNG_RW in -lSDL_image... no
checking for glBegin in -lGL... no
checking for SDL_mixer.h... no
checking for Mix_OpenAudio in -lSDL_mixer... no
checking how to run the C preprocessor... gcc -E
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
checking mxml.h usability... no
checking mxml.h presence... no
checking for mxml.h... no
configure: error: Cannot find Mini-XML header file.
stretch@Lappy-X:~/Desktop/dreamchess-0.2.0$ make
make: *** No targets specified and no makefile found.  Stop.
stretch@Lappy-X:~/Desktop/dreamchess-0.2.0$ 

```

---

### Post by stretch4 on 2014-08-07
So, I was missing libmxml-dev and libmxml1. I installed them and I got it to commpile. Now when I run "make install" to install it, it doesn't work...

```

stretch@Lappy-X:~/Desktop/dreamchess-0.2.0$ make install
Making install in desktop
make[1]: Entering directory `/home/stretch/Desktop/dreamchess-0.2.0/desktop'
make[2]: Entering directory `/home/stretch/Desktop/dreamchess-0.2.0/desktop'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/stretch/Desktop/dreamchess-0.2.0/desktop'
make[1]: Leaving directory `/home/stretch/Desktop/dreamchess-0.2.0/desktop'
Making install in doc
make[1]: Entering directory `/home/stretch/Desktop/dreamchess-0.2.0/doc'
make[2]: Entering directory `/home/stretch/Desktop/dreamchess-0.2.0/doc'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/stretch/Desktop/dreamchess-0.2.0/doc'
make[1]: Leaving directory `/home/stretch/Desktop/dreamchess-0.2.0/doc'
Making install in src
make[1]: Entering directory `/home/stretch/Desktop/dreamchess-0.2.0/src'
make  install-recursive
make[2]: Entering directory `/home/stretch/Desktop/dreamchess-0.2.0/src'
Making install in libs
make[3]: Entering directory `/home/stretch/Desktop/dreamchess-0.2.0/src/libs'
Making install in gamegui
make[4]: Entering directory `/home/stretch/Desktop/dreamchess-0.2.0/src/libs/gamegui'
make[5]: Entering directory `/home/stretch/Desktop/dreamchess-0.2.0/src/libs/gamegui'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/home/stretch/Desktop/dreamchess-0.2.0/src/libs/gamegui'
make[4]: Leaving directory `/home/stretch/Desktop/dreamchess-0.2.0/src/libs/gamegui'
Making install in minizip
make[4]: Entering directory `/home/stretch/Desktop/dreamchess-0.2.0/src/libs/minizip'
make[5]: Entering directory `/home/stretch/Desktop/dreamchess-0.2.0/src/libs/minizip'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/home/stretch/Desktop/dreamchess-0.2.0/src/libs/minizip'
make[4]: Leaving directory `/home/stretch/Desktop/dreamchess-0.2.0/src/libs/minizip'
make[4]: Entering directory `/home/stretch/Desktop/dreamchess-0.2.0/src/libs'
make[5]: Entering directory `/home/stretch/Desktop/dreamchess-0.2.0/src/libs'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/home/stretch/Desktop/dreamchess-0.2.0/src/libs'
make[4]: Leaving directory `/home/stretch/Desktop/dreamchess-0.2.0/src/libs'
make[3]: Leaving directory `/home/stretch/Desktop/dreamchess-0.2.0/src/libs'
Making install in dreamer
make[3]: Entering directory `/home/stretch/Desktop/dreamchess-0.2.0/src/dreamer'
make[4]: Entering directory `/home/stretch/Desktop/dreamchess-0.2.0/src/dreamer'
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'dreamer' '/usr/local/bin/dreamer'
/usr/bin/install: cannot remove &#8216;/usr/local/bin/dreamer&#8217;: Permission denied
make[4]: *** [install-binPROGRAMS] Error 1
make[4]: Leaving directory `/home/stretch/Desktop/dreamchess-0.2.0/src/dreamer'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/stretch/Desktop/dreamchess-0.2.0/src/dreamer'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/stretch/Desktop/dreamchess-0.2.0/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/stretch/Desktop/dreamchess-0.2.0/src'
make: *** [install-recursive] Error 1
stretch@Lappy-X:~/Desktop/dreamchess-0.2.0$ 

```

---

### Post by steeldriver on 2014-08-07
You need root permissions to install / remove / modify files in the target directory /usr/local/bin

```

**sudo** make install

```

---

