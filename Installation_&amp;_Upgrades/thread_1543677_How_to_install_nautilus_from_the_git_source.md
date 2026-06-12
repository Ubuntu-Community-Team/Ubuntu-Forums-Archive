---
title: "How to install nautilus from the git source ?"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by hakzsam on 2010-08-01
Hi all,

I tried to install nautilus from the git source but I have several problems.

I downloaded the source code with the following command :
```
git clone git://git.gnome.org/nautilus
```

Then, I run the autogen.sh script :
```
cd nautilus && ./autogen.sh
```

> /usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.65
checking for automake >= 1.9...
  testing automake-1.11... found 1.11.1
checking for libtool >= 1.5...
  testing libtoolize... found 2.2.6b
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.25.12
checking for intltool >= 0.30...
  testing intltoolize... found 0.41.0
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
checking for gtk-doc >= 1.0...
  testing gtkdocize... found 1.14
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./ltmain.sh'
libtoolize: putting macros in AC_CONFIG_MACRO_DIR, `m4'.
libtoolize: copying file `m4/libtool.m4'
libtoolize: copying file `m4/ltoptions.m4'
libtoolize: copying file `m4/ltsugar.m4'
libtoolize: copying file `m4/ltversion.m4'
libtoolize: copying file `m4/lt~obsolete.m4'
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

Running intltoolize...
Running gtkdocize...
Running aclocal-1.11...
Running autoconf...
Running autoheader...
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader: 
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows one to define a template without
autoheader: WARNING: `acconfig.h':
autoheader: 
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader: 		[Define if a function `main' is needed.])
autoheader: 
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
Running automake-1.11...
configure.in:54: installing `./config.guess'
configure.in:54: installing `./config.sub'
configure.in:30: installing `./install-sh'
configure.in:30: installing `./missing'
cut-n-paste-code/libegg/Makefile.am: installing `./depcomp'
libnautilus-extension/Makefile.am:67: HAVE_INTROSPECTION does not appear in AM_CONDITIONAL
Makefile.am: installing `./INSTALL'

Btw, I don't understand the warning messages, so, if someone could explain me...

And I run the ./configure script:
```
./configure
```

> checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
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
checking for an ANSI C-conforming const... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
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
checking for pkg-config... /usr/bin/pkg-config
checking for floor in -lm... yes
checking pkg-config is at least version 0.9.0... yes
checking for ALL... configure: error: Package requirements (
	glib-2.0		>= 2.25.12
	gnome-desktop-3.0	>= 2.29.91
	gthread-2.0
	gio-unix-2.0
	gio-2.0
	pango			>= 1.1.2
	gtk+-3.0		>= 2.90.5
	libxml-2.0		>= 2.4.7
	gail-3.0		>= 2.90.5
) were not met:

No package 'gnome-desktop-3.0' found
No package 'gtk+-3.0' found
No package 'gail-3.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ALL_CFLAGS
and ALL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.



Thanks in advance for your help ! :)

---

### Post by dino99 on 2010-08-01
[https://help.ubuntu.com/community/Git](https://help.ubuntu.com/community/Git)

---

### Post by hakzsam on 2010-08-01
Thanks for the link dino99, but I don't have problems with git. 

I have problems with dependencies when I run the ./configure script and I don't understand how to install correctly those libraries.

---

### Post by dino99 on 2010-08-01
when you download this nautilus snapshot, you might install from its path (download location)

as its a dependencies issue, have you read the git doc about nautilus, are these dependencies available on your system, or is it a path issue ?

---

