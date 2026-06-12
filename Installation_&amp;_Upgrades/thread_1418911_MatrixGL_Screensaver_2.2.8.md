---
title: "MatrixGL Screensaver 2.2.8"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by -Protos- on 2010-03-01
Hi fellas,

Not new to ubuntu, tried some previous distros .... and one of them had an AWESOME matrix screensaver (the one with the faces) well I see that it is no longer in the default list.

I found it at sourceforge .... downloaded and ./configured. Ran into a lot of issues with missing packages .... which I have mostly resolved ... however I still am missing some.. and I am stuck.

link to screensaver [http://sourceforge.net/projects/matrixgl/](http://sourceforge.net/projects/matrixgl/)

Any and all help greatly appreciated. 

protos@Protos-Linux:~/Downloads/matrixgl-2.2.8$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
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
checking whether gcc and cc understand -c and -o together... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
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
checking for size_t... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for memset... yes
checking for X... libraries , headers 
checking for XOpenDisplay in -lX11... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking OpenGL/gl.h usability... no
checking OpenGL/gl.h presence... no
checking for OpenGL/gl.h... no
checking for OpenGL library... -lGL
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking GL/glu.h usability... yes
checking GL/glu.h presence... yes
checking for GL/glu.h... yes
checking OpenGL/glu.h usability... no
checking OpenGL/glu.h presence... no
checking for OpenGL/glu.h... no
checking for OpenGL Utility library... -lGLU
checking for varargs GLU tesselator callback function type... no
checking if xscreensaver feature is enabled.. yes
checking for xscreensaver hack directory... /usr/lib/xscreensaver
checking for xscreensaver config directory... /usr/share/xscreensaver/config
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing depfiles commands
protos@Protos-Linux:~/Downloads/matrixgl-2.2.8$

---

### Post by hansdown on 2010-03-01
Hi -Protos-

It's called matrix view, and it should be in the screen saver folder.

---

### Post by -Protos- on 2010-03-01
Thanks hansdown, 

I had uninstalled gnomescreensaver in favor of xscreensaver.

You wouldn't know how to edit preferences for this screensaver would you ??? I would like to make some adjustments.

---

### Post by hansdown on 2010-03-01
If you mean adjust when and how it activates, then click

power management.

Hope that helps.

---

### Post by -Protos- on 2010-03-02
Sorry no.... I meant to be able to modify certain aspects of it as you can do with xscreensaver.  

Actually I would still like to install the 2.2.8 version ....

---

### Post by hansdown on 2010-03-02
Unfortunately, my compiling skills are not well honed.

What packages are missing?

---

