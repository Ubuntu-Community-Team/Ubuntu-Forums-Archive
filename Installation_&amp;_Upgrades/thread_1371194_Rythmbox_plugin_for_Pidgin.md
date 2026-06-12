---
title: "Rythmbox plugin for Pidgin"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by Wandels on 2010-01-03
Does anyone know how I can get my current playing song in my Pidgin status?
I allready found some solutions for an AIM-account ([http://ubuntuforums.org/showthread.php?t=622264](http://ubuntuforums.org/showthread.php?t=622264)) but I'm using MSN.

Isn't there a simple procedure or so?


Thanks

---

### Post by Wandels on 2010-01-04
I tryed this:
[http://code.google.com/p/pidgin-musictracker/](http://code.google.com/p/pidgin-musictracker/)

```
ben@ben-desktop:~$ cd ~/Desktop
ben@ben-desktop:~/Desktop$ cd pidgin-m*
ben@ben-desktop:~/Desktop/pidgin-musictracker-0.4.20$ ./configure
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
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PIDGIN... yes
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.0.0... yes (version 2.22.3)
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.0.0... yes (version 2.18.3)
checking for DBUS... yes
checking for XMMSCLIENT... no
checking for pcre_exec in -lpcre... no
configure: error:
[B]*** PCRE library is required to build pidgin-musictracker
*** Please make sure you have the PCRE development files installed
*** The latest version of PCRE is always available at http://www.pcre.org/[/B]

```

Okay, so I download PCRE 8.00 from here: [ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/](ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/)

Then I reinstall the musictracker but it still doesn't seem to work.

---

