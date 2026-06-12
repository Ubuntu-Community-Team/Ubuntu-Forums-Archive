---
title: "Magic layout software installation problem.. Please help.."
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by dineshbabu on 2007-05-22
[COLOR="Green"][B]I am trying to install Magic layout software.. First i used ./configure command in the terminal and it got configured sucessfully.. Then i gave make and make install commands.. It got executed but with some mistakes..

I wil post all the comments of ./configure,make and make install commands here.. Please go through and help me to resolve the problem.. I am very new to linux and hence i dont know much.. Please help me..[/B][/COLOR]
[COLOR="Red"]
Here is the comments when i ran '/configure:[/COLOR]

[B]dinesh@Dinesh:~/magic-7.4.34$ ./configure
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
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking for glXCreateContext in -lGL... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
configure: creating ./config.status
config.status: creating defs.mak

-----------------------------------------------------------
Configuration Summary (principle requirements):

X11:          yes
OpenGL:       yes
Tcl/Tk:       yes
BLT:          yes
-----------------------------------------------------------

Use 'make' to compile and 'make install' to install.

Errors may not be printed to stdout:  see files 'make.log' 
  and 'install.log' for complete error summary.

-----------------------------------------------------------[/B]

[COLOR="Red"]Then here is the output when i ran make command:[/COLOR]

[B]dinesh@Dinesh:~/magic-7.4.34$ make
--- errors and warnings logged in file make.log
--- making modules
--- making Tcl shared libraries
--- making magic Tcl library (tclmagic.so)
[/B]

[COLOR="Red"]Then finally i ran make install command.. Here is the comments:[/COLOR]


[B]dinesh@Dinesh:~/magic-7.4.34$ make install
--- installing executable to /usr/local/bin
--- installing runtime files to /usr/local/lib
rm: cannot remove `windows7.glyphs': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/windows7.glyphs': Permission denied
rm: cannot remove `windows11.glyphs': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/windows11.glyphs': Permission denied
rm: cannot remove `windows14.glyphs': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/windows14.glyphs': Permission denied
rm: cannot remove `windows22.glyphs': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/windows22.glyphs': Permission denied
make[2]: *** [install-tcl] Error 1
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.7bit.dstyle': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.7bit.std.cmap': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.24bit.dstyle': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.24bit.std.cmap': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.7bit.mraster_dstyle': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.7bit.mraster.cmap': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.OpenGL.dstyle': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.OpenGL.std.cmap': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/minimum.tech': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/gdsquery.tech': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/scmos.tech': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/scmos-tm.tech': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/scmos-sub.tech': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/scmosWR.tech': Permission denied
make[2]: *** [install-tcl] Error 1
rm: cannot remove `/usr/local/bin/magic': Permission denied
make[2]: *** [/usr/local/bin/magic.sh] Error 1
/usr/bin/ld: cannot find -lXmu
collect2: ld returned 1 exit status
make[2]: *** [tclmagic.so] Error 1
rm: cannot remove `/usr/local/bin/magic': Permission denied
make[2]: *** [/usr/local/bin/magic.sh] Error 1
make[1]: *** [install-tcl-real] Error 2
make: *** [install-tcl] Error 2[/B]


Please please help me.. Thanks in advance! :)

---

### Post by pxwpxw on 2007-05-22
Try

sudo make install

---

### Post by larrybalz on 2007-05-23
Thanks for the info pxwpxw it worked perfectly well when i was trying to  install another software:popcorn:

---

