---
title: "Installing E17 using easy_e17.sh gives problem with emotion"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by chaosx9 on 2010-05-06
Well, using the full packagelist, emotion gives me this error (copied from the log):

```
-------------------------------------------------------------------------------
EASY_E17 1.3.2 CMD: ./autogen.sh --prefix=/opt/e17  
-------------------------------------------------------------------------------
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for library containing strerror... none required
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether to build emotion_test binary... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether to build documentation... yes
checking for doxygen... no
WARNING:
The doxygen program was not found in your execute path.
You may have doxygen installed somewhere not covered by your path.

If this is the case make sure you have the packages installed, AND
that the doxygen program is in your execute path (see your
shell manual page on setting the $PATH environment variable), OR
alternatively, specify the program to use with --with-doxygen.
configure: WARNING: no doxygen detected. Documentation will not be built
checking for EMOTION... yes
checking for EMOTION_BIN... yes
checking for ECORE_X... yes
checking for ECORE_FB... no
checking if should provide Edje EXTERNAL support...... auto
checking for EDJE_EXTERNAL... yes
checking for ANSI C header files... (cached) yes
checking for an ANSI C-conforming const... yes
checking whether byte ordering is bigendian... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for __attribute__... yes
checking for XINE... no
checking whether to enable Xine module built... no
checking for GSTREAMER... no
checking whether to enable Gstreamer module built... no
checking for VLC... no
checking whether to enable VLC module built... no
configure: error: Xine, Gstreamer or VLC backends must be selected to build Emotion
```

---

### Post by lechien73 on 2010-05-06
The installer was unable to find Xine, GStreamer or VLC:
```
Xine, Gstreamer or VLC backends must be selected to build Emotion
```
You can install VLC, for example, by making sure you have a multiverse mirror listed in your /etc/apt/sources.list and then typing:
```
sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc
```
Then try the installation again.

---

### Post by chaosx9 on 2010-05-06
I had VLC installed already, and running normally. I'm not sure why the script isn't detecting it

---

