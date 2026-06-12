---
title: "Upgrade package"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by dodgingspam on 2008-04-22
I'd like to upgrade BlueFish, to the latest release. I've downloaded the latest .GZ package. How do I go about upgrading the current package on Ubuntu?

---

### Post by Pumalite on 2008-04-22
Try this:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by dodgingspam on 2008-04-22
I ran ./configure and got the following output:
> 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

So, what do I do now with that C error?

---

### Post by louieb on 2008-04-22
Do you have the c compiler installed?
If not install package build-essential

If you do what does the config.log say?

---

### Post by dodgingspam on 2008-04-22
OK, I've installed build-essential using Synaptics tool and ran > ./configure again. It did not choke this time and seems like it went through some sort of installation, however I do not see the change in the version of the software that I'm trying to update. Also looking back at the log of what wetnthrough I see that it was not quite a success. Here's the full output:
> 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
svs@svs-laptop:~/Desktop/bf/bluefish-unstable-1.1.6$ 
svs@svs-laptop:~/Desktop/bf/bluefish-unstable-1.1.6$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking for msgfmt... no
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking whether NLS is requested... yes
checking for msgfmt... (cached) no
checking for gmsgfmt... no
./configure: line 6413: no: command not found
./configure: line 6418: no: command not found
checking for xgettext... no
checking for msgmerge... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognize dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... no
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for library containing strerror... none required
checking for inline... inline
checking for a BSD-compatible install... /usr/bin/install -c
checking for gdk-pixbuf-csource... no
checking for xmlcatalog... /usr/bin/xmlcatalog
checking for update-desktop-database... /usr/bin/update-desktop-database
checking for update-mime-database... /usr/bin/update-mime-database
configure: The given systems XML catalog ${prefix}/etc/xml/catalog seems to be unavailable.
configure: We will not try to update it after installation.
checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BFREQ... configure: error: Package requirements (gtk+-2.0 >= 2.6 gmodule-2.0 >= 2.6 gobject-2.0 glib-2.0 pango gdk-pixbuf-2.0 gdk-2.0 gnome-vfs-2.0 >= 2.10 libxml-2.0) were not met:

No package 'gtk+-2.0' found
No package 'gmodule-2.0' found
No package 'gobject-2.0' found
No package 'glib-2.0' found
No package 'pango' found
No package 'gdk-pixbuf-2.0' found
No package 'gdk-2.0' found
No package 'gnome-vfs-2.0' found
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BFREQ_CFLAGS
and BFREQ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
 

I'm ready to call it quits...

---

### Post by dodgingspam on 2008-04-23
I've found the following in configure file:
[PHP]
BFREQ_required="gtk+-2.0 >= 2.6 \
gmodule-2.0 >= 2.6 \
gobject-2.0 \
glib-2.0 \
pango \
gdk-pixbuf-2.0 \
gdk-2.0 \
gnome-vfs-2.0 >= 2.10 \
libxml-2.0"


pkg_failed=no
{ echo "$as_me:$LINENO: checking for BFREQ" >&5
echo $ECHO_N "checking for BFREQ... $ECHO_C" >&6; }

if test -n "$PKG_CONFIG"; then
    if test -n "$BFREQ_CFLAGS"; then
        pkg_cv_BFREQ_CFLAGS="$BFREQ_CFLAGS"
    else
        if test -n "$PKG_CONFIG" && \
    { (echo "$as_me:$LINENO: \$PKG_CONFIG --exists --print-errors \"\$BFREQ_required\"") >&5
  ($PKG_CONFIG --exists --print-errors "$BFREQ_required") 2>&5
  ac_status=$?
  echo "$as_me:$LINENO: \$? = $ac_status" >&5
  (exit $ac_status); }; then
  pkg_cv_BFREQ_CFLAGS=`$PKG_CONFIG --cflags "$BFREQ_required" 2>/dev/null`
else
  pkg_failed=yes
fi
    fi
else
	pkg_failed=untried
fi
if test -n "$PKG_CONFIG"; then
    if test -n "$BFREQ_LIBS"; then
        pkg_cv_BFREQ_LIBS="$BFREQ_LIBS"
    else
        if test -n "$PKG_CONFIG" && \
    { (echo "$as_me:$LINENO: \$PKG_CONFIG --exists --print-errors \"\$BFREQ_required\"") >&5
  ($PKG_CONFIG --exists --print-errors "$BFREQ_required") 2>&5
  ac_status=$?
  echo "$as_me:$LINENO: \$? = $ac_status" >&5
  (exit $ac_status); }; then
  pkg_cv_BFREQ_LIBS=`$PKG_CONFIG --libs "$BFREQ_required" 2>/dev/null`
else
  pkg_failed=yes
fi
    fi
else
	pkg_failed=untried
fi



if test $pkg_failed = yes; then

if $PKG_CONFIG --atleast-pkgconfig-version 0.20; then
        _pkg_short_errors_supported=yes
else
        _pkg_short_errors_supported=no
fi
        if test $_pkg_short_errors_supported = yes; then
	        BFREQ_PKG_ERRORS=`$PKG_CONFIG --short-errors --errors-to-stdout --print-errors "$BFREQ_required"`
        else
	        BFREQ_PKG_ERRORS=`$PKG_CONFIG --errors-to-stdout --print-errors "$BFREQ_required"`
        fi
	# Put the nasty error message in config.log where it belongs
	echo "$BFREQ_PKG_ERRORS" >&5

	{ { echo "$as_me:$LINENO: error: Package requirements ($BFREQ_required) were not met:

$BFREQ_PKG_ERRORS

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BFREQ_CFLAGS
and BFREQ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
" >&5
echo "$as_me: error: Package requirements ($BFREQ_required) were not met:

$BFREQ_PKG_ERRORS

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BFREQ_CFLAGS
and BFREQ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
" >&2;}
   { (exit 1); exit 1; }; }
elif test $pkg_failed = untried; then
	{ { echo "$as_me:$LINENO: error: The pkg-config script could not be found or is too old.  Make sure it
is in your PATH or set the PKG_CONFIG environment variable to the full
path to pkg-config.

Alternatively, you may set the environment variables BFREQ_CFLAGS
and BFREQ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

To get pkg-config, see <http://pkg-config.freedesktop.org/>.
See \`config.log' for more details." >&5
echo "$as_me: error: The pkg-config script could not be found or is too old.  Make sure it
is in your PATH or set the PKG_CONFIG environment variable to the full
path to pkg-config.

Alternatively, you may set the environment variables BFREQ_CFLAGS
and BFREQ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

To get pkg-config, see <http://pkg-config.freedesktop.org/>.
See \`config.log' for more details." >&2;}
   { (exit 1); exit 1; }; }
else
	BFREQ_CFLAGS=$pkg_cv_BFREQ_CFLAGS
	BFREQ_LIBS=$pkg_cv_BFREQ_LIBS
        { echo "$as_me:$LINENO: result: yes" >&5
echo "${ECHO_T}yes" >&6; }
	:
fi
[/PHP]

How do I adhear to the following suggestion:
> 
Alternatively, you may set the environment variables BFREQ_CFLAGS
and BFREQ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


---

### Post by dodgingspam on 2008-04-23
any takers?

---

### Post by Pumalite on 2008-04-23
'See the pkg-config man page for more details'

---

### Post by dodgingspam on 2008-04-23
I found /usr/bin/pkg-config but I can't even open it. Are you talking about some other file?

---

### Post by Pumalite on 2008-04-23
It might not be there, but try in your Terminal:
man pkg-config

---

### Post by dodgingspam on 2008-04-23
OK, that worked, but I'm clueles what am I supposed to do with it?...

---

### Post by Pumalite on 2008-04-23
Read it and apply what you learn from it.

---

### Post by dodgingspam on 2008-04-25
Here's where the trouble starts:
> checking for BFREQ... configure: error: Package requirements (gtk+-2.0 >= 2.6 gmodule-2.0 >= 2.6 gobject-2.0 glib-2.0 pango gdk-pixbuf-2.0 gdk-2.0 gnome-vfs-2.0 >= 2.10 libxml-2.0) were not met:

No package 'gtk+-2.0' found
No package 'gmodule-2.0' found
No package 'gobject-2.0' found
No package 'glib-2.0' found
No package 'pango' found
No package 'gdk-pixbuf-2.0' found
No package 'gdk-2.0' found
No package 'gnome-vfs-2.0' found
No package 'libxml-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BFREQ_CFLAGS
and BFREQ_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details. 

I looked in synaptic and do not even see those packages (dah... they're missing). I think it's getting too complicated for my taste. If I start messing with all that I may break something... I'll just wait until the roll out new stable version. Should not be more then another year. :)

---

