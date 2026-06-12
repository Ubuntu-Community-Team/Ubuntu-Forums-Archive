---
title: "Desmume 0.9.6-1 is giving me errors"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by d4rkn355 on 2010-12-29
I Downloaded Desmume 0.9.6-1 hoping to see if the cheat fieatures have been, you know, upgraded, and when i try to compile using the ./configure command, it gives me an annoying error, and im pretty much clueless about this one :| (I am fairly new to the Ubuntu/Linux experience).

The error line im not getting is:
```
grep: po/Makefile.in: No such file or directory
config.status: error: po/Makefile.in.in was not created by intltoolize.
```

The overall *./configure* command gives me this:
```
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking whether the C++ compiler works... yes
checking for C++ compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
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
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether NLS is requested... yes
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.1
checking for XML::Parser... ok
checking for gzopen in -lz... yes
checking for zzip_open in -lzzip... yes
checking whether zzip use void * as second parameter... yes
checking for sdl-config... no
checking for sdl11-config... no
checking GL/gl.h usability... no
checking GL/gl.h presence... no
checking for GL/gl.h... no
checking GL/glu.h usability... no
checking GL/glu.h presence... no
checking for GL/glu.h... no
checking for main in -ldl... yes
checking for main in -lGL... no
checking for main in -lOSMesa... no
checking for pkg-config... pkg-config
checking for GLIB... yes
checking for GTK... yes
checking for GTKGLEXT... no
checking for GTHREAD... yes
checking for LIBGLADE... no
checking for LUA... no
checking for LUA... no
checking for ALSA... no
checking for LIBAGG... no
checking for update-desktop-database... /usr/bin/update-desktop-database
configure: WARNING: Antigrain library not found, HUD will be disabled
checking whether to enable maintainer-specific portions of Makefiles... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/cli/Makefile
config.status: creating src/cli/doc/Makefile
config.status: creating src/cocoa/Makefile
config.status: creating src/gtk/Makefile
config.status: creating src/gtk/doc/Makefile
config.status: creating src/gtk-glade/Makefile
config.status: creating src/gtk-glade/doc/Makefile
config.status: creating src/wx/Makefile
config.status: creating src/gdbstub/Makefile
config.status: creating autopackage/default.apspec
config.status: executing depfiles commands
config.status: executing po/stamp-it commands
grep: po/Makefile.in: No such file or directory
config.status: error: po/Makefile.in.in was not created by intltoolize.

```

OR do i have to Yes Every No here? I did some googling around a found an archive in this forum, but it didn't help, the links weren't, you know, working.

Thanks for the help ;)

---

