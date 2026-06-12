---
title: "HELP: adjusting PKG_CONFIG_PATH environment variable"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by honey toast on 2010-02-18
Hi everyone, 

I am trying to manually install Anjuta onto my laptop. I downloaded the file from the Anjuta website and it is the latest build 2.28.2.0. I untarred it into my home directory and am now going through the process of trying to compile it so that I can 'make/install' it. From terminal, in my home dir, I then 'cd' anjuta-2.28.2.0 and then ./configure which then begins to initialize before it stops at this message...

 ```

Duncan@Duncan-laptop://home/anjuta-2.28.2.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether ln -s works... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking gnome-doc-utils >= 0.3.2... yes
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
checking how to run the C preprocessor... gcc -E
checking whether gcc and cc understand -c and -o together... yes
checking whether gcc understands -Wno-sign-compare... yes
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare
checking what language compliance flags to pass to the C compiler... 
checking for library containing strerror... none required
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking return type of signal handlers... void
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB... configure: error: Package requirements (glib-2.0 >= 2.16.0 gobject-2.0 >= 2.16.0 gmodule-2.0 >= 2.16.0 gthread-2.0 >= 2.16.0 gio-2.0 >= 2.16.0 unique-1.0 >= 1.0.0) were not met:

No package 'unique-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.



```I have already install build essentials. I have tried to find unique-1.0 in synaptic, but cannot locate it-well, there are variants in synaptic, but not the exact same file.

I'm not sure where to go from here. Thanks for reading this.

Also I have tried echo  $PKG_CONFIG_PATH to view the darn thing, but it is not present.
Nothing available for echo $GLIB_CFLAGS or GLIB_LIBS either.

---

### Post by honey toast on 2010-02-18
**** it

---

### Post by kc4mts on 2010-03-20
In the quote below it looks as if the package unique needs to be version 1.0 or better, so if you found a variant that is a newer (higher) version try to "sudo apt-get install unique-" (the higher version number)"-dev". The dev means you want the development package.


> **honey toast said:**
> Hi everyone, 

I am trying to manually install Anjuta onto my laptop. I downloaded the file from the Anjuta website and it is the latest build 2.28.2.0. I untarred it into my home directory and am now going through the process of trying to compile it so that I can 'make/install' it. From terminal, in my home dir, I then 'cd' anjuta-2.28.2.0 and then ./configure which then begins to initialize before it stops at this message...

 ```


checking for GLIB... configure: error: Package requirements (glib-2.0 >= 2.16.0 gobject-2.0 >= 2.16.0 gmodule-2.0 >= 2.16.0 gthread-2.0 >= 2.16.0 gio-2.0 >= 2.16.0 unique-1.0 >= 1.0.0) were not met:

No package 'unique-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GLIB_CFLAGS
and GLIB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.



```I have already install build essentials. I have tried to find unique-1.0 in synaptic, but cannot locate it-well, there are variants in synaptic, but not the exact same file.

I'm not sure where to go from here. Thanks for reading this.

Also I have tried echo  $PKG_CONFIG_PATH to view the darn thing, but it is not present.
Nothing available for echo $GLIB_CFLAGS or GLIB_LIBS either.

---

