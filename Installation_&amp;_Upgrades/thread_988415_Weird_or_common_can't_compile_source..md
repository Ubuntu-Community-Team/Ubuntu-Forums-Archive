---
title: "Weird or common: can't compile source."
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by merk113z on 2008-11-20
I downloaded Firestarter from its official web site, because the one from the repositories didn't work. It was showing that there was no connection established, although the connection was fine. (Please, help me solve this problem, too. I'm new to Linux). 

Anyway, I downloaded a tar.gz archive, extracted it on the desktop and entered it through the terminal. Before that I installed the build-essentials, by the way. 
The ./configure part went fine, I guess:

-------------------------------------------------------
checking for intltool >= 0.30... 0.31.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
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
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler... 
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for gconftool-2... /usr/bin/gconftool-2
checking for pkg-config... /usr/bin/pkg-config
checking for libgnome-2.0 >= 2.0.0
                  libgnomeui-2.0 >= 2.0.0
                  gtk+-2.0 >= 2.4.0
                  gnome-vfs-2.0 >= 2.6.0
		  libglade-2.0 >= 2.3.6... Package libgnome-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnome-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnome-2.0' found Package libgnomeui-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libgnomeui-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libgnomeui-2.0' found Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found Package gnome-vfs-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gnome-vfs-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gnome-vfs-2.0' found Package libglade-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libglade-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libglade-2.0' found
configure: error: Library requirements (libgnome-2.0 >= 2.0.0
                  libgnomeui-2.0 >= 2.0.0
                  gtk+-2.0 >= 2.4.0
                  gnome-vfs-2.0 >= 2.6.0
		  libglade-2.0 >= 2.3.6) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
------------------------------------------------------

However, the 'make' command returned this error: make: *** No targets specified and no makefile found.  Stop. 
The INSTALL document in the archive says ./configure will make such file but apparently it doesn't. After a few unsuccessful tries I entered a src directory in the archive and tried again. Same thing. 
Please,help.

---

### Post by oldos2er on 2008-11-20
It looks like ./configure errored out with a dependency issue. That's what configure: error: Library requirements (libgnome-2.0 >= 2.0.0 is telling you. You need the package libglade-2.0-dev.

---

### Post by merk113z on 2008-11-21
Library requirements (libgnome-2.0 >= 2.0.0
                  libgnomeui-2.0 >= 2.0.0
                  gtk+-2.0 >= 2.4.0
                  gnome-vfs-2.0 >= 2.6.0
		  libglade-2.0 >= 2.3.6) 


How to get them all at once, or I should download them one by one? 
And what exactly are those files and libraries?

---

### Post by mtausig on 2008-11-21
Open a terminal and type

sudo apt-get install package1 package2 ....

Or start the graphical package manager "synaptic", search for the packages you want there and install them.

---

### Post by oldos2er on 2008-11-21
> **merk113z said:**
> Library requirements (libgnome-2.0 >= 2.0.0
                  libgnomeui-2.0 >= 2.0.0
                  gtk+-2.0 >= 2.4.0
                  gnome-vfs-2.0 >= 2.6.0
          libglade-2.0 >= 2.3.6) 


How to get them all at once, or I should download them one by one? 
And what exactly are those files and libraries?

 As was suggested, use Synaptic, which will give you descriptions, and you can install them all at once.

 Usually in source code there is a README and/or INSTALL file that tells you of any dependencies you need.

---

### Post by merk113z on 2008-11-22
All the packages are already installed on my computer, but it still displays the same error. However, in Synaptic the names of those programs are not the same. For every one I've searched but libglade there was something installed. Since there was nothing like libglade 2.0, I clicked on libglade 2-ruby 1.8. The same error appeared again.

 Where is this PKG_CONFIG_PATH and how to add these programs' directories to it ? You think this will solve the problem?

---

### Post by taurus on 2008-11-22
You also need to install the -dev packages.

---

### Post by merk113z on 2008-11-23
How?  

-----------------------------------------
apt-get install libglade-2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libglade-2.0-dev
-----------------------------------------

I'm not exactly advanced, please, talk like you talk to a newbie.

---

