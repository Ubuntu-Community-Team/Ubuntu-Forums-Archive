---
title: "GLIB errors for libnetdude-0.12 source compile"
date: 2014-03-17
forum: Installation &amp; Upgrades
---

### Post by mccalleyt on 2014-03-17
I am trying to compile and install libnetdude 0.12 for netdude  0.5.1 in kubuntu 13.10 x64. I get this error on the ./configure stage of  install. I don't know how to set the path variable for glib_config. Is  there a known deb file for install on my version? I have tried looking  but nothing yet. Can someone please help me out?

```

checking for glib-config... no
checking for glib... no
*** The glib-config script installed by glib could not be found
*** If glib was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: Cannot find glib: Is glib-config in path? 


```

Thanks,
mccalleyt

---

### Post by steeldriver on 2014-03-17
I don't see any mention of a glib-config script anywhere in packages.ubuntu.com - perhaps it is only applicable to other platforms? The usual way for configure scripts to find glib in Ubuntu is via pkg-config e.g. for glib-2.0 (I suspect that's what the second line 'checking for glib... no' is doing)

```
$ pkg-config --modversion glib-2.0
2.32.4

```

Do you have the prerequisite dev package(s) installed (e.g. libglib2.0-dev)

---

### Post by mccalleyt on 2014-03-17
Here is what I get when I try to do the configure stage. I don't know how to set the variables or which ones to set.

```

user@Computer:~/NewSoftware/netdude/libnetdude-0.12$ ./configure
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
checking whether make sets $(MAKE)... (cached) yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking which extension is used for runtime loadable modules... .so
checking which variable specifies run-time module search path... LD_LIBRARY_PATH
checking for the default library search path... /lib64 /usr/lib64 /lib  /usr/lib /usr/lib/i386-linux-gnu/mesa /lib/i386-linux-gnu  /usr/lib/i386-linux-gnu /lib/i686-linux-gnu /usr/lib/i686-linux-gnu  /usr/local/lib /lib/x86_64-linux-gnu /usr/lib/x86_64-linux-gnu  /usr/lib/x86_64-linux-gnu/mesa-egl /usr/lib/x86_64-linux-gnu/mesa /lib32  /usr/lib32 /libx32 /usr/libx32 
checking for library containing dlopen... -ldl
checking for dlerror... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dld_link in -ldld... no
checking for _ prefix in compiled symbols... no
checking whether deplibs are loaded by dlopen... yes
checking for argz.h... yes
checking for error_t... yes
checking for argz_add... yes
checking for argz_append... yes
checking for argz_count... yes
checking for argz_create_sep... yes
checking for argz_insert... yes
checking for argz_next... yes
checking for argz_stringify... yes
checking if argz actually works... yes
checking whether libtool supports -dlopen/-dlpreopen... yes
checking for ltdl.h... yes
checking whether lt_dlinterface_register is declared... yes
checking for lt_dladvise_preload in -lltdl... yes
checking where to find libltdl headers... 
checking where to find libltdl library... -lltdl
checking for unistd.h... (cached) yes
checking for dl.h... no
checking for sys/dl.h... no
checking for dld.h... no
checking for mach-o/dyld.h... no
checking for dirent.h... yes
checking for closedir... yes
checking for opendir... yes
checking for readdir... yes
checking for strlcat... no
checking for strlcpy... no
checking host system type... (cached) x86_64-unknown-linux-gnu
checking whether byte ordering is bigendian... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for lt_ptr_t... no
checking for lt_dladvise... yes
checking for glib-config... no
checking for glib... no
*** The glib-config script installed by glib could not be found
*** If glib was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: Cannot find glib: Is glib-config in path?

```

Here is what I got from pkg-config --modversion glib-2.0.

```

user@Computer:~/NewSoftware/netdude/libnetdude-0.12$ pkg-config --modversion glib-2.0
2.38.1
user@Computer:~/NewSoftware/netdude/libnetdude-0.12$

```

I'm just frustrated with the fact I can't just configure and compile a simple program and be able to use it. I would like to find deb packages that are ready for Kubuntu/Ubuntu 13.10.

Thanks,
mccalleyt

---

### Post by steeldriver on 2014-03-17
Hmm... the latest reference I can find to glib-config is in Hardy Heron - so I'm wondering whether libnetdude-0.12 is just too old (the tarball is dated 2010) to build without modification on 13.10?

---

### Post by mccalleyt on 2014-03-17
IYHO it would be a waste to try to adapt this ware to be used on 13.10? I guess I could look for other wares that can do what NetDUDE can do. I know sometimes it is preferable to use the old tools because the new ones are the same thing but cost money to get and use. I do remember seeing somewhere in my research that Hardy was the last release to have it. I was just hoping that maybe there was a way to install it that was out there. I looked for an answer to my question for awhile but none of the fixes they suggested worked. I even went as far to look at similar but unrelated forums and nothing.

Thank you,
mccalleyt

---

### Post by mccalleyt on 2014-03-17
> **steeldriver said:**
> Hmm... the latest reference I can find to glib-config is in Hardy Heron - so I'm wondering whether libnetdude-0.12 is just too old (the tarball is dated 2010) to build without modification on 13.10?
 
I would think there is a simple way to get the configure script to see the new location of glib or maybe just a way to make the script think everything is ok and good to procede.

Thanks,
mccalleyt

---

### Post by steeldriver on 2014-03-17
Well... after a bit of playing it seems you can keep the configure script happy by creating a script called 'glib-config' containing

```

#!/bin/bash

pkg-config "$@" glib-2.0

```

Make it executable (*chmod +x glib-config*) and put it somewhere on your PATH (I suggest */usr/local/bin*)

However I would be extremely surprised if there were not a bunch of other incompatibilities that need to be fixed before you get a successful build.

EDIT: surprisingly it did build on my 13.10 VM (after installing libpcap-dev and libpcapnav0-dev) - no idea how to test it though

---

### Post by mccalleyt on 2014-03-18
I now have this issue with netdude0.5.1 ./configure. I have no idea what to put in the gtk-config file and where to put it. 
```

user@computer:~/NewSoftware/netdude/netdude-0.5.1$ ./configure
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
checking whether make sets $(MAKE)... (cached) yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking which extension is used for runtime loadable modules... .so
checking which variable specifies run-time module search path... LD_LIBRARY_PATH
checking for the default library search path... /lib64 /usr/lib64 /lib /usr/lib /usr/lib/i386-linux-gnu/mesa /lib/i386-linux-gnu /usr/lib/i386-linux-gnu /lib/i686-linux-gnu /usr/lib/i686-linux-gnu /usr/local/lib /lib/x86_64-linux-gnu /usr/lib/x86_64-linux-gnu /usr/lib/x86_64-linux-gnu/mesa-egl /usr/lib/x86_64-linux-gnu/mesa /lib32 /usr/lib32 /libx32 /usr/libx32 
checking for library containing dlopen... -ldl
checking for dlerror... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dld_link in -ldld... no
checking for _ prefix in compiled symbols... no
checking whether deplibs are loaded by dlopen... yes
checking for argz.h... yes
checking for error_t... yes
checking for argz_add... yes
checking for argz_append... yes
checking for argz_count... yes
checking for argz_create_sep... yes
checking for argz_insert... yes
checking for argz_next... yes
checking for argz_stringify... yes
checking if argz actually works... yes
checking whether libtool supports -dlopen/-dlpreopen... yes
checking for ltdl.h... yes
checking whether lt_dlinterface_register is declared... yes
checking for lt_dladvise_preload in -lltdl... yes
checking where to find libltdl headers... 
checking where to find libltdl library... -lltdl
checking for unistd.h... (cached) yes
checking for dl.h... no
checking for sys/dl.h... no
checking for dld.h... no
checking for mach-o/dyld.h... no
checking for dirent.h... yes
checking for closedir... yes
checking for opendir... yes
checking for readdir... yes
checking for strlcat... no
checking for strlcpy... no
checking host system type... (cached) x86_64-unknown-linux-gnu
checking whether byte ordering is bigendian... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for gtk-config... no
checking for gtk... no
*** The gtk-config script installed by gtk could not be found
*** If gtk was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: Cannot find GTK: Is gtk-config in path?

```

Thanks,
mccalleyt

Sorry I made the decision last year to get rid of windowz on all machines I own. I am glad I did, but I'm still learning.

---

### Post by steeldriver on 2014-03-18
Have you tried the same trick? i.e an executable script file called **gtk-config** somewhere on your PATH containing 

```

#!/bin/bash

pkg-config "$@" **gtk+**-2.0

```

Of course this assumes you have installed the **libgtk2.0-dev** package

---

### Post by mccalleyt on 2014-03-19
No I didn't I wasn't sure where to put it and what to put in the script. I really appreciate it. Where is a good place to start to learn the file system structure and locations of software and what applications are in what packages. I know that I can use Muon Package Manager to see all installed files in a package, but that is too much work to do for all packages.

---

### Post by steeldriver on 2014-03-19
TBH most configure scripts 'just work' and most source code distributions are pretty good about listing dependencies - this is a bit of a special case. My *guess* is that the glib-config and gtk-config scripts are either deprecated (no longer used) or 'foreign' (i.e. used by other distros, possibly RedHat, but not by Ubuntu / Debian) and the netdude package maintainer(s) simply haven't got around to testing the source build on Debian/Ubuntu.

The fix I suggested is an ugly hack - really what it needs is someone who understands the GNU autoconf / automake system to re-write the checks so that they use pkg-config natively (at least on Ubuntu) - I know just enough to be dangerous i.e. to look in the **configure.in** file 
```

dnl ##################################################
dnl # Check for Glib.
dnl ##################################################
AC_ARG_WITH(glib,
            AC_HELP_STRING([--with-glib=DIR], [Use glib in <DIR>]),
            [CFLAGS="$CFLAGS -I$withval/include"
            LIBS="-L$withval/lib $LIBS"])

AC_PATH_GENERIC(glib,, [
    AC_SUBST(glib_libs)
    AC_SUBST(glib_cflags)],
    AC_MSG_ERROR(Cannot find glib: Is glib-config in path?))
[B]glib_libs=`glib-config --libs`
glib_cflags=`glib-config --cflags`
[/B]
```

and know just about enough about pkg-config to figure out that it might be possible to replace those by

```

pkg-config --libs glib-2.0
pkg-config --cflags glib-2.0

```

---

### Post by mccalleyt on 2014-03-20
Yet again I am stumped again. I found the file under /usr/local/include/libnetdude/0.12/libnd.h however I am not seeing what I need to do to remedy this. I guess I just need a good mentor. I am looking to learn as much as I can so that if I get this job I applied for (I am pretty much gaureented to get) working for a local sheriff's office I will be able to take up managing their linux systems they are thinking on installing.

```

user@computer:~/NewSoftware/netdude/netdude-0.5.1$ sudo ./configure
[sudo] password for user: 
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
checking whether make sets $(MAKE)... (cached) yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking which extension is used for runtime loadable modules... .so
checking which variable specifies run-time module search path... LD_LIBRARY_PATH
checking for the default library search path... /lib64 /usr/lib64 /lib /usr/lib /usr/lib/i386-linux-gnu/mesa /lib/i386-linux-gnu /usr/lib/i386-linux-gnu /lib/i686-linux-gnu /usr/lib/i686-linux-gnu /usr/local/lib /lib/x86_64-linux-gnu /usr/lib/x86_64-linux-gnu /usr/lib/x86_64-linux-gnu/mesa-egl /usr/lib/x86_64-linux-gnu/mesa /lib32 /usr/lib32 /libx32 /usr/libx32 
checking for library containing dlopen... -ldl
checking for dlerror... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dld_link in -ldld... no
checking for _ prefix in compiled symbols... no
checking whether deplibs are loaded by dlopen... yes
checking for argz.h... yes
checking for error_t... yes
checking for argz_add... yes
checking for argz_append... yes
checking for argz_count... yes
checking for argz_create_sep... yes
checking for argz_insert... yes
checking for argz_next... yes
checking for argz_stringify... yes
checking if argz actually works... yes
checking whether libtool supports -dlopen/-dlpreopen... yes
checking for ltdl.h... yes
checking whether lt_dlinterface_register is declared... yes
checking for lt_dladvise_preload in -lltdl... yes
checking where to find libltdl headers... 
checking where to find libltdl library... -lltdl
checking for unistd.h... (cached) yes
checking for dl.h... no
checking for sys/dl.h... no
checking for dld.h... no
checking for mach-o/dyld.h... no
checking for dirent.h... yes
checking for closedir... yes
checking for opendir... yes
checking for readdir... yes
checking for strlcat... no
checking for strlcpy... no
checking host system type... (cached) x86_64-unknown-linux-gnu
checking whether byte ordering is bigendian... no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for gtk-config... /usr/local/bin/gtk-config
checking for gtk... yes
checking for lndtool... /usr/local/bin/lndtool
/usr/local/bin/lndtool: error while loading shared libraries: libnetdude.so.0: cannot open shared object file: No such file or directory
/usr/local/bin/lndtool: error while loading shared libraries: libnetdude.so.0: cannot open shared object file: No such file or directory
/usr/local/bin/lndtool: error while loading shared libraries: libnetdude.so.0: cannot open shared object file: No such file or directory
checking fam.h usability... no
checking fam.h presence... no
checking for fam.h... no
checking for main in -lfam... no
checking for lt_ptr_t... no
checking for gtkdoc-mkdb... false
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating plugins/Makefile
config.status: creating plugins/ChecksumFix/Makefile
config.status: creating plugins/BPF-Filter/Makefile
config.status: creating protocols/Makefile
config.status: creating protocols/arp/Makefile
config.status: creating protocols/ether/Makefile
config.status: creating protocols/fddi/Makefile
config.status: creating protocols/icmp/Makefile
config.status: creating protocols/ip/Makefile
config.status: creating protocols/pcap/Makefile
config.status: creating protocols/linux-sll/Makefile
config.status: creating protocols/snap/Makefile
config.status: creating protocols/tcp/Makefile
config.status: creating protocols/udp/Makefile
config.status: creating protocols/vlan/Makefile
config.status: creating pixmaps/Makefile
config.status: creating doc/Makefile
config.status: creating doc/netdude-manual/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing mkhtml commands
=== configuring in libltdl (/home/user/NewSoftware/netdude/netdude-0.5.1/libltdl)
configure: running /bin/bash ./configure --disable-option-checking '--prefix=/usr/local'  --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking which extension is used for runtime loadable modules... .so
checking which variable specifies run-time module search path... LD_LIBRARY_PATH
checking for the default library search path... /lib64 /usr/lib64 /lib /usr/lib /usr/lib/i386-linux-gnu/mesa /lib/i386-linux-gnu /usr/lib/i386-linux-gnu /lib/i686-linux-gnu /usr/lib/i686-linux-gnu /usr/local/lib /lib/x86_64-linux-gnu /usr/lib/x86_64-linux-gnu /usr/lib/x86_64-linux-gnu/mesa-egl /usr/lib/x86_64-linux-gnu/mesa /lib32 /usr/lib32 /libx32 /usr/libx32 
checking for library containing dlopen... -ldl
checking for dlerror... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dld_link in -ldld... no
checking for _ prefix in compiled symbols... no
checking whether deplibs are loaded by dlopen... yes
checking for argz.h... yes
checking for error_t... yes
checking for argz_add... yes
checking for argz_append... yes
checking for argz_count... yes
checking for argz_create_sep... yes
checking for argz_insert... yes
checking for argz_next... yes
checking for argz_stringify... yes
checking if argz actually works... yes
checking whether libtool supports -dlopen/-dlpreopen... yes
checking for unistd.h... (cached) yes
checking for dl.h... no
checking for sys/dl.h... no
checking for dld.h... no
checking for mach-o/dyld.h... no
checking for dirent.h... yes
checking for closedir... yes
checking for opendir... yes
checking for readdir... yes
checking for strlcat... no
checking for strlcpy... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands

         Netdude 0.5 Configuration Summary
====================================================

  libnetdude configuration: /usr/local/bin/lndtool
  FAM support:              no
  Debugging enabled:        no

  Setup finished. Now run:

  $ make
  # make install

  (or use gmake when make on your platform isn't GNU make)

user@configure:~/NewSoftware/netdude/netdude-0.5.1$ make
make  all-recursive
make[1]: Entering directory `/home/user/NewSoftware/netdude/netdude-0.5.1'
Making all in libltdl
make[2]: Entering directory `/home/user/NewSoftware/netdude/netdude-0.5.1/libltdl'
make  all-am
make[3]: Entering directory `/home/user/NewSoftware/netdude/netdude-0.5.1/libltdl'
/bin/bash ./libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -DLT_CONFIG_H='<config.h>' -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl   -g -O2 -MT dlopen.lo -MD -MP -MF .deps/dlopen.Tpo -c -o dlopen.lo `test -f 'loaders/dlopen.c' || echo './'`loaders/dlopen.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. "-DLT_CONFIG_H=<config.h>" -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl -g -O2 -MT dlopen.lo -MD -MP -MF .deps/dlopen.Tpo -c loaders/dlopen.c  -fPIC -DPIC -o .libs/dlopen.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. "-DLT_CONFIG_H=<config.h>" -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl -g -O2 -MT dlopen.lo -MD -MP -MF .deps/dlopen.Tpo -c loaders/dlopen.c -o dlopen.o >/dev/null 2>&1
mv -f .deps/dlopen.Tpo .deps/dlopen.Plo
/bin/bash ./libtool --tag=CC   --mode=link gcc  -g -O2 -module -avoid-version  -o dlopen.la  dlopen.lo -ldl -ldl 
libtool: link: ar cru .libs/dlopen.a .libs/dlopen.o 
libtool: link: ranlib .libs/dlopen.a
libtool: link: ( cd ".libs" && rm -f "dlopen.la" && ln -s "../dlopen.la" "dlopen.la" )
/bin/bash ./libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -DLTDLOPEN=libltdlc -DLT_CONFIG_H='<config.h>' -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl   -g -O2 -MT libltdlc_la-preopen.lo -MD -MP -MF .deps/libltdlc_la-preopen.Tpo -c -o libltdlc_la-preopen.lo `test -f 'loaders/preopen.c' || echo './'`loaders/preopen.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -DLTDLOPEN=libltdlc "-DLT_CONFIG_H=<config.h>" -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl -g -O2 -MT libltdlc_la-preopen.lo -MD -MP -MF .deps/libltdlc_la-preopen.Tpo -c loaders/preopen.c  -fPIC -DPIC -o .libs/libltdlc_la-preopen.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -DLTDLOPEN=libltdlc "-DLT_CONFIG_H=<config.h>" -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl -g -O2 -MT libltdlc_la-preopen.lo -MD -MP -MF .deps/libltdlc_la-preopen.Tpo -c loaders/preopen.c -o libltdlc_la-preopen.o >/dev/null 2>&1
mv -f .deps/libltdlc_la-preopen.Tpo .deps/libltdlc_la-preopen.Plo
/bin/bash ./libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -DLTDLOPEN=libltdlc -DLT_CONFIG_H='<config.h>' -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl   -g -O2 -MT libltdlc_la-lt__alloc.lo -MD -MP -MF .deps/libltdlc_la-lt__alloc.Tpo -c -o libltdlc_la-lt__alloc.lo `test -f 'lt__alloc.c' || echo './'`lt__alloc.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -DLTDLOPEN=libltdlc "-DLT_CONFIG_H=<config.h>" -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl -g -O2 -MT libltdlc_la-lt__alloc.lo -MD -MP -MF .deps/libltdlc_la-lt__alloc.Tpo -c lt__alloc.c  -fPIC -DPIC -o .libs/libltdlc_la-lt__alloc.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -DLTDLOPEN=libltdlc "-DLT_CONFIG_H=<config.h>" -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl -g -O2 -MT libltdlc_la-lt__alloc.lo -MD -MP -MF .deps/libltdlc_la-lt__alloc.Tpo -c lt__alloc.c -o libltdlc_la-lt__alloc.o >/dev/null 2>&1
mv -f .deps/libltdlc_la-lt__alloc.Tpo .deps/libltdlc_la-lt__alloc.Plo
/bin/bash ./libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -DLTDLOPEN=libltdlc -DLT_CONFIG_H='<config.h>' -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl   -g -O2 -MT libltdlc_la-lt_dlloader.lo -MD -MP -MF .deps/libltdlc_la-lt_dlloader.Tpo -c -o libltdlc_la-lt_dlloader.lo `test -f 'lt_dlloader.c' || echo './'`lt_dlloader.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -DLTDLOPEN=libltdlc "-DLT_CONFIG_H=<config.h>" -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl -g -O2 -MT libltdlc_la-lt_dlloader.lo -MD -MP -MF .deps/libltdlc_la-lt_dlloader.Tpo -c lt_dlloader.c  -fPIC -DPIC -o .libs/libltdlc_la-lt_dlloader.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -DLTDLOPEN=libltdlc "-DLT_CONFIG_H=<config.h>" -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl -g -O2 -MT libltdlc_la-lt_dlloader.lo -MD -MP -MF .deps/libltdlc_la-lt_dlloader.Tpo -c lt_dlloader.c -o libltdlc_la-lt_dlloader.o >/dev/null 2>&1
mv -f .deps/libltdlc_la-lt_dlloader.Tpo .deps/libltdlc_la-lt_dlloader.Plo
/bin/bash ./libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -DLTDLOPEN=libltdlc -DLT_CONFIG_H='<config.h>' -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl   -g -O2 -MT libltdlc_la-lt_error.lo -MD -MP -MF .deps/libltdlc_la-lt_error.Tpo -c -o libltdlc_la-lt_error.lo `test -f 'lt_error.c' || echo './'`lt_error.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -DLTDLOPEN=libltdlc "-DLT_CONFIG_H=<config.h>" -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl -g -O2 -MT libltdlc_la-lt_error.lo -MD -MP -MF .deps/libltdlc_la-lt_error.Tpo -c lt_error.c  -fPIC -DPIC -o .libs/libltdlc_la-lt_error.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -DLTDLOPEN=libltdlc "-DLT_CONFIG_H=<config.h>" -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl -g -O2 -MT libltdlc_la-lt_error.lo -MD -MP -MF .deps/libltdlc_la-lt_error.Tpo -c lt_error.c -o libltdlc_la-lt_error.o >/dev/null 2>&1
mv -f .deps/libltdlc_la-lt_error.Tpo .deps/libltdlc_la-lt_error.Plo
/bin/bash ./libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -DLTDLOPEN=libltdlc -DLT_CONFIG_H='<config.h>' -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl   -g -O2 -MT libltdlc_la-ltdl.lo -MD -MP -MF .deps/libltdlc_la-ltdl.Tpo -c -o libltdlc_la-ltdl.lo `test -f 'ltdl.c' || echo './'`ltdl.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -DLTDLOPEN=libltdlc "-DLT_CONFIG_H=<config.h>" -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl -g -O2 -MT libltdlc_la-ltdl.lo -MD -MP -MF .deps/libltdlc_la-ltdl.Tpo -c ltdl.c  -fPIC -DPIC -o .libs/libltdlc_la-ltdl.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -DLTDLOPEN=libltdlc "-DLT_CONFIG_H=<config.h>" -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl -g -O2 -MT libltdlc_la-ltdl.lo -MD -MP -MF .deps/libltdlc_la-ltdl.Tpo -c ltdl.c -o libltdlc_la-ltdl.o >/dev/null 2>&1
mv -f .deps/libltdlc_la-ltdl.Tpo .deps/libltdlc_la-ltdl.Plo
/bin/bash ./libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -DLTDLOPEN=libltdlc -DLT_CONFIG_H='<config.h>' -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl   -g -O2 -MT libltdlc_la-slist.lo -MD -MP -MF .deps/libltdlc_la-slist.Tpo -c -o libltdlc_la-slist.lo `test -f 'slist.c' || echo './'`slist.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -DLTDLOPEN=libltdlc "-DLT_CONFIG_H=<config.h>" -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl -g -O2 -MT libltdlc_la-slist.lo -MD -MP -MF .deps/libltdlc_la-slist.Tpo -c slist.c  -fPIC -DPIC -o .libs/libltdlc_la-slist.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -DLTDLOPEN=libltdlc "-DLT_CONFIG_H=<config.h>" -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl -g -O2 -MT libltdlc_la-slist.lo -MD -MP -MF .deps/libltdlc_la-slist.Tpo -c slist.c -o libltdlc_la-slist.o >/dev/null 2>&1
mv -f .deps/libltdlc_la-slist.Tpo .deps/libltdlc_la-slist.Plo
/bin/bash ./libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I.  -DLT_CONFIG_H='<config.h>' -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl   -g -O2 -MT lt__strl.lo -MD -MP -MF .deps/lt__strl.Tpo -c -o lt__strl.lo lt__strl.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. "-DLT_CONFIG_H=<config.h>" -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl -g -O2 -MT lt__strl.lo -MD -MP -MF .deps/lt__strl.Tpo -c lt__strl.c  -fPIC -DPIC -o .libs/lt__strl.o
libtool: compile:  gcc -DHAVE_CONFIG_H -I. "-DLT_CONFIG_H=<config.h>" -DLTDL -I. -I. -Ilibltdl -I./libltdl -I./libltdl -g -O2 -MT lt__strl.lo -MD -MP -MF .deps/lt__strl.Tpo -c lt__strl.c -o lt__strl.o >/dev/null 2>&1
mv -f .deps/lt__strl.Tpo .deps/lt__strl.Plo
/bin/bash ./libtool --tag=CC   --mode=link gcc  -g -O2 -no-undefined -dlpreopen dlopen.la   -o libltdlc.la  libltdlc_la-preopen.lo libltdlc_la-lt__alloc.lo libltdlc_la-lt_dlloader.lo libltdlc_la-lt_error.lo libltdlc_la-ltdl.lo libltdlc_la-slist.lo lt__strl.lo -ldl 
libtool: link: rm -f .libs/libltdlc.nm .libs/libltdlc.nmS .libs/libltdlc.nmT
libtool: link: (cd .libs && gcc -g -O2 -c -fno-builtin  -fPIC -DPIC "libltdlcS.c")
libtool: link: rm -f ".libs/libltdlcS.c" ".libs/libltdlc.nm" ".libs/libltdlc.nmS" ".libs/libltdlc.nmT"
libtool: link: (cd .libs/libltdlc.lax/dlopen.a && ar x "/home/mccalleyt/NewSoftware/netdude/netdude-0.5.1/libltdl/./.libs/dlopen.a")
libtool: link: ar cru .libs/libltdlc.a .libs/libltdlc_la-preopen.o .libs/libltdlc_la-lt__alloc.o .libs/libltdlc_la-lt_dlloader.o .libs/libltdlc_la-lt_error.o .libs/libltdlc_la-ltdl.o .libs/libltdlc_la-slist.o .libs/lt__strl.o .libs/libltdlcS.o  .libs/libltdlc.lax/dlopen.a/dlopen.o 
libtool: link: ranlib .libs/libltdlc.a
libtool: link: rm -fr .libs/libltdlc.lax
libtool: link: ( cd ".libs" && rm -f "libltdlc.la" && ln -s "../libltdlc.la" "libltdlc.la" )
make[3]: Leaving directory `/home/user/NewSoftware/netdude/netdude-0.5.1/libltdl'
make[2]: Leaving directory `/home/user/NewSoftware/netdude/netdude-0.5.1/libltdl'
Making all in src
make[2]: Entering directory `/home/user/NewSoftware/netdude/netdude-0.5.1/src'
gcc -DHAVE_CONFIG_H -I. -I.. -I.. -I../libltdl -I../src -pthread -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/harfbuzz -DLIBNETDUDE_CFLAGS="\"\"" -DGTK_CFLAGS="\"-pthread -I/usr/include/gtk-2.0 -I/usr/lib/x86_64-linux-gnu/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/harfbuzz  \"" -W -Wall     -g -O2 -MT nd_debug.o -MD -MP -MF .deps/nd_debug.Tpo -c -o nd_debug.o nd_debug.c
In file included from nd_debug.c:29:0:
./nd.h:32:19: fatal error: libnd.h: No such file or directory
 #include <libnd.h>
                   ^
compilation terminated.
make[2]: *** [nd_debug.o] Error 1
make[2]: Leaving directory `/home/user/NewSoftware/netdude/netdude-0.5.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user/NewSoftware/netdude/netdude-0.5.1'
make: *** [all] Error 2

```

---

### Post by steeldriver on 2014-03-20
That happened to me as well - I think it just means that the build of netdude is not finding the installation of libnetdude. Did you remember to **make install** in the libnetdude directory (not just make) **before **trying to make netdude?

It may help to delete both your libnetdude-0.12 and netdude-0.5.1 directories and unpack fresh copies from the tarballs, then configure / make / make install libnetdude, **then **try to configure / make netdude (I think sometimes failed configs leave things in a state that a subsequent 'good' ./configure doesn't quite fix) now that you have the glib-config and gtk-config hacks in place.

FWIW I always use configure flag **--prefix=/usr/local** so that there is no chance of overwriting 'system' files (although /usr/local may be the default prefix for the package)

EDIT: **DON'T USE sudo FOR THE ./configure OR make STAGES!** sudo is ONLY required for the final 'make install'

(in particular, using sudo for the ./configure may cause problems with root-owned makefiles)

---

### Post by mccalleyt on 2014-03-20
I did as you said but I got the exact same error during the make phase.

---

