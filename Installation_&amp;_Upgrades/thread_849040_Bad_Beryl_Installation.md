---
title: "Bad Beryl Installation"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by Infatuas on 2008-07-04
Hello All,

I'm fairly new to the linux world which i'm sure most have heard many times. I'm trying to install Beryl on the latest Ubuntu release. I got stuck at one point then fixed it and now i'm stuck again.

```
infatuas@infidel:~$ cd Desktop
infatuas@infidel:~/Desktop$ cd beryl-core-0.2.1
infatuas@infidel:~/Desktop/beryl-core-0.2.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
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
checking for ANSI C header files... (cached) yes
checking for stdlib.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking for intltool >= 0.35.0... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBBERYLDECORATION... configure: error: Package requirements (xrender >= 0.8.4) were not met:

No package 'xrender' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBBERYLDECORATION_CFLAGS
and LIBBERYLDECORATION_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

Any help would be greatly appreciated.

---

### Post by chewearn on 2008-07-04
There is no need to install Beryl, and it's obsolete anyway.

Beryl and Compiz have merged, and it's now called Compiz Fusion.  If you have ubuntu 8.04 (with gnome), you already have compiz by default.  What you need to do is enable a video driver that support 3D graphics.  Then, enable the Special Effects.

Tell us what graphics card you have, and we can proceed from there.
.

---

### Post by Infatuas on 2008-07-04
I have a compaq presario v6105nr laptop with intel graphics. The only real reason i like Beryl is because of the 3d Desktop cube. I'd appreciate the help.

---

### Post by oldos2er on 2008-07-04
The latest Ubuntu comes with compiz-fusion installed by default. You can get the cube by installing the package "compizconfig-settings-manager" and changing the settings from there.

---

### Post by Infatuas on 2008-07-05
excellent! Thank you so much for your help. I am trying to remove beryl at the moment but i can't find the package name, i always went to add/remove and cannot locate the package manually. any tips?

---

### Post by chewearn on 2008-07-05
Looking at the screen capture in post #1, I would say beryl has not been installed.  Simple delete "beryl-core-0.2.1" subdirectory in your desktop would do it.

---

### Post by Infatuas on 2008-07-05
it was definately installed an functional. i re installed ubuntu, i took the full plunge and ditched microsoft windows haha. figured what the hell, and this is the first linux os that is really stable on my laptop. Well, thanks for your help. i'm going to install that package above and see how it works. :) thanks

---

### Post by sayakb on 2008-07-05
It seems very well that you are fond of eyecandy and GUI effects. Here's a thread to make it even better: [http://ubuntuforums.org/showthread.php?t=841886](http://ubuntuforums.org/showthread.php?t=841886)

---

### Post by Infatuas on 2008-07-05
Wow, it's working well now! I'm loving the eyecandy but ultimately I want to learn the command line stuff. I'm extremely comfortable within a windows platforms DOS and so on, so the foundation is their it's just the commands are different and much more powerful. Does anyone have a place to start? Example, linux for dummies web based learning, lol.

---

### Post by chewearn on 2008-07-05
Some guides, direct from google.

[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

Scripting beginners guide:
[http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/index.html)

Advanced scripting:
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

