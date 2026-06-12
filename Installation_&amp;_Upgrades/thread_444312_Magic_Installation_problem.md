---
title: "Magic Installation problem"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by barath on 2007-05-15
My friend is having a pblm while installing magic software when he typed ./configure he gotthe following error 

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
checking for library containing strerror... none required
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for gm4... no
checking for gnum4... no
checking for m4... /usr/bin/m4
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
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
checking for void *... yes
checking size of void *... 4
checking for unsigned int... yes
checking size of unsigned int... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking for unsigned long long... yes
checking size of unsigned long long... 8
checking whether byte ordering is bigendian... no
checking for ANSI C header files... (cached) yes
checking for setenv... yes
checking for putenv... yes
checking for vfork... yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking param.h usability... no
checking param.h presence... no
checking for param.h... no
checking paths.h usability... yes
checking paths.h presence... yes
checking for paths.h... yes
checking for va_copy... yes
checking for __va_copy... yes
checking for round in -lm... yes
checking for roundf in -lm... yes
checking for gcore... /usr/bin/gcore
checking for csh... /bin/csh
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for tclConfig.sh... /usr/lib/tcl8.4/tclConfig.sh
checking for tkConfig.sh... /usr/lib/tk8.4/tkConfig.sh
checking for wish executable... /usr/bin/wish
checking for tclsh executable... /usr/bin/tclsh
checking GL/gl.h usability... no
checking GL/gl.h presence... no
checking for GL/gl.h... no
GL header files not found, disabling OpenGL
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
configure: creating ./config.status
config.status: creating defs.mak

-----------------------------------------------------------
Configuration Summary (principle requirements):

X11:          yes
OpenGL:       no

  OpenGL graphics are considerably better than the standard 8-bit
  and 24-bit X11 graphics, provided that you have a video card and
  driver supporting accelerated OpenGL graphics.  If you get this
  message, you may need to download OpenGL libraries and header
  files, which are usually available from the video card manufacturer.
  Magic with un-accelerated OpenGL, such as using Mesa GL without
  a supported graphics card, is usually a very bad combination.

Tcl/Tk:       yes
BLT:          no

  Tcl/Tk magic uses the BLT package to create a tree diagram
  of the cell hierarchy in a design.  Without it, this option
  is unavailable.  Consider installing the BLT package.

-----------------------------------------------------------

Use 'make' to compile and 'make install' to install.

Errors may not be printed to stdout:  see files 'make.log' 
  and 'install.log' for complete error summary.

How to install OpenGl and BLT ......
Thank you in advance

---

### Post by Topsiho on 2007-05-15
blt is in synaptic. About the OpenGL libraries I don' t know, probably you should follow the suggestion that was given in that long list of messages ...

Topsiho

---

### Post by kvprashant on 2008-03-21
the problem maybe due to missing header files of openGL libraries

For OpenGL try:

installing mesa-common-dev from synaptic (or)

hit sudo apt-get install freeglut3 freeglut3-dev in terminal

---

