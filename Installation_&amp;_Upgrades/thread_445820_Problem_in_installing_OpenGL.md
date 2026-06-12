---
title: "Problem in installing OpenGL"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by dineshbabu on 2007-05-16
I am trying to install one software called Magic.. 

While i typed ./configure in terminal,i got the following message saying i need to have OpenGL! Please see the error message and please help me what to do next.. Please help me..

Here is the error message:

[b]checking build system type... i686-pc-linux-gnu
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
BLT:          yes[/b]

Please help me.. Thanks in advance..

---

### Post by dineshbabu on 2007-05-16
I guess the problem lies in some GL header files as far as i infer from the error message!

[B]"checking GL/gl.h usability... no
checking GL/gl.h presence... no
checking for GL/gl.h... no
GL header files not found, disabling OpenGL"[/B]

I am new to Linux and i have no idea about OpenGL and others.. Please help me in what to do next.. Please...

---

### Post by moma on 2007-05-16
What package contains the **gl.h** file ?

$ [COLOR="SeaGreen"]dpkg -S gl.h [/COLOR]
.....
mesa-common-dev: /usr/include/GL/gl.h

The answer is: install mesa-common-dev package.  
------------------

But I usually just install the [GLUT]("http://freeglut.sourceforge.net/") package because it comes with all necessary dependencies for OpenGL development.  So run:

$ [COLOR="SeaGreen"]sudo apt-get install freeglut3 freeglut3-dev[/COLOR]
----------------------

ps. Code::Blocks IDE 
[http://ubuntuforums.org/showthread.php?p=1962696#post1962696](http://ubuntuforums.org/showthread.php?p=1962696#post1962696)

---

### Post by dineshbabu on 2007-05-16
Thanks a lot.. i wil try that..

---

### Post by dineshbabu on 2007-05-16
> **moma said:**
> What package contains the **gl.h** file ?

$ [COLOR="SeaGreen"]dpkg -S gl.h [/COLOR]
.....
mesa-common-dev: /usr/include/GL/gl.h

The answer is: install mesa-common-dev package.  
------------------

But I usually just install the [GLUT]("http://freeglut.sourceforge.net/") package because it comes with all necessary dependencies for OpenGL development.  So run:

$ [COLOR="SeaGreen"]sudo apt-get install freeglut3 freeglut3-dev[/COLOR]
----------------------

ps. Code::Blocks IDE 
[http://ubuntuforums.org/showthread.php?p=1962696#post1962696](http://ubuntuforums.org/showthread.php?p=1962696#post1962696)

This is also not working.. :(

Please help me..

This is the error report i got: 
"dinesh@Dinesh:~/magic-7.4.34$ sudo apt-get install freeglut3 freeglut3-dev
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

Please help me..

---

### Post by Enverex on 2007-05-16
> **dineshbabu said:**
> I guess the problem lies in some GL header files as far as i infer from the error message!

[B]"checking GL/gl.h usability... no
checking GL/gl.h presence... no
checking for GL/gl.h... no
GL header files not found, disabling OpenGL"[/B]

I am new to Linux and i have no idea about OpenGL and others.. Please help me in what to do next.. Please...

You need to install your graphics driver header files. For nVidia it's the nvidia-glx-dev package (if you're using nvidia-glx). Or the -dev package for fglrx if you're using that, etc.

> **dineshbabu said:**
> This is also not working.. :(

Please help me..

This is the error report i got: 
"dinesh@Dinesh:~/magic-7.4.34$ sudo apt-get install freeglut3 freeglut3-dev
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

Please help me..

This means you have Synaptic or some other Apt program already open, close that first.

---

