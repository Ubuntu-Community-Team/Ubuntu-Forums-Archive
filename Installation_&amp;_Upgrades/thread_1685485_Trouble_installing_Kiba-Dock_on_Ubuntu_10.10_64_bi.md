---
title: "Trouble installing Kiba-Dock on Ubuntu 10.10 64 bit"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by TurtleKing on 2011-02-10
Following this how-to on installing kiba-dock:
[http://ubuntuforums.org/showthread.php?t=554127]("http://ubuntuforums.org/showthread.php?t=554127")
I get after the first command:
howto:
```
sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev
```
My result:
```
E: Unable to locate package libglitz-glx1-dev
E: Unable to locate package libglitz1-dev

```
I went ahead and ignore this, but later on I got stuck on this section:
howto:
```
cd kiba-plugins/ 
CC="gcc -fPIC" ./autogen.sh --prefix=/usr --libdir=/usr/lib64 
sudo make install 
cd ..
```
My result after this command:
```
checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.in: tracing
autoreconf: running: libtoolize --install --copy
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.in and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
autoreconf: Leaving directory `.'

Running 'glib-gettextize'... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.


Running 'intltoolize'...

Running './configure --prefix=/usr --libdir=/usr/lib64' ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc -fPIC
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc -fPIC accepts -g... yes
checking for gcc -fPIC option to accept ISO C89... none needed
checking dependency style of gcc -fPIC... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc -fPIC
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc -fPIC accepts -g... (cached) yes
checking for gcc -fPIC option to accept ISO C89... (cached) none needed
checking dependency style of gcc -fPIC... (cached) gcc3
checking how to run the C preprocessor... gcc -fPIC -E
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc -fPIC... /usr/bin/ld
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
checking command to parse /usr/bin/nm -B output from gcc -fPIC object... ok
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
checking if gcc -fPIC supports -fno-rtti -fno-exceptions... no
checking for gcc -fPIC option to produce PIC... -fPIC -DPIC
checking if gcc -fPIC PIC flag -fPIC -DPIC works... yes
checking if gcc -fPIC static flag -static works... yes
checking if gcc -fPIC supports -c -o file.o... yes
checking if gcc -fPIC supports -c -o file.o... (cached) yes
checking whether the gcc -fPIC linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for ANSI C header files... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking whether NLS is requested... yes
checking for intltool >= 0.35.0... 0.41.1 found
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
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for gettimeofday... yes
checking for memset... yes
checking for sqrt... no
checking for strrchr... yes
checking for strstr... yes
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for KIBA_DOCK... no
configure: error: Package requirements (kiba-dock = 9999) were not met:

No package 'kiba-dock' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables KIBA_DOCK_CFLAGS
and KIBA_DOCK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```
I get the same for the command after, any help on how to fix this problem?

---

### Post by TurtleKing on 2011-02-10
bump

---

### Post by TurtleKing on 2011-02-11
Anybody tried installing this on Ubuntu 10.10 64 bit?

---

