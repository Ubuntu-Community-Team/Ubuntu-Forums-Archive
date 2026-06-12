---
title: "Installing gThumb image viewer program getting errors, some packages missing"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by abcuser on 2009-11-28
Hi,
on Ubuntu 9.10 I would like to install the latest gThumb from development trunk. I have followed instructions at:
[http://live.gnome.org/gthumb](http://live.gnome.org/gthumb)

1. Install dependencies
```
sudo apt-get install git-core autoconf libgnome2-dev libgtk2.0-dev libgnomeui-dev libexiv2-dev libglade2-dev gnome-common libgphoto2-2-dev libgnomedesktop2.20-cil gnome-devel
```
installed succesfully.

2. Download software:
```
git clone git://git.gnome.org/gthumb 
```

It looks ok, output is:
```

Initialized empty Git repository in /home/abcuser/Temp/gthumb/.git/
remote: Counting objects: 25451, done.
remote: Compressing objects: 100% (7717/7717), done.
remote: Total 25451 (delta 21164), reused 21042 (delta 17675)
Receiving objects: 100% (25451/25451), 12.50 MiB | 79 KiB/s, done.
Resolving deltas: 100% (21164/21164), done.

```

3. Change directory
```
cd gthumb
```

4. Checkout
```
git checkout -b ext origin/ext
```
It looks ok:
```

Branch ext set up to track remote branch ext from origin.
Switched to a new branch 'ext'

```

5. Autogenerate
```

./autogen.sh --prefix=/usr CFLAGS="-ggdb" 

```

Some error messages:
```

/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.64
checking for automake >= 1.8...
  testing automake-1.11... found 1.11
checking for libtool >= 1.5...
  testing libtoolize... found 2.2.6
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.22.2
checking for intltool >= 0.30...
  testing intltoolize... found 0.41.0
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
checking for gnome-doc-utils >= 0.4.2...
  testing gnome-doc-prepare... found 0.18.0
checking for gnome-common >= 2.3.0...
  testing gnome-doc-common... found 2.28.0
Checking for required M4 macros...
Checking for forbidden M4 macros...
Processing ./configure.ac
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
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running gnome-doc-common...
Running gnome-doc-prepare...
You should add the contents of '/usr/share/aclocal/gnome-doc-utils.m4' to 'aclocal.m4'.
Putting files in AC_CONFIG_MACRO_DIR, 'm4'.
Running aclocal-1.11...
Running autoconf...
Running autoheader...
Running automake-1.11...
configure.ac:23: installing `./config.guess'
configure.ac:23: installing `./config.sub'
configure.ac:9: installing `./install-sh'
configure.ac:9: installing `./missing'
copy-n-paste/Makefile.am: installing `./depcomp'
Running ./configure --prefix=/usr CFLAGS=-ggdb ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
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
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for glib-genmarshal... /usr/bin/glib-genmarshal
checking for glib-mkenums... /usr/bin/glib-mkenums
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
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
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking how to run the C++ preprocessor... g++ -E
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
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking gnome-doc-utils >= 0.3.2... yes
checking whether gcc understands -Wno-sign-compare... yes
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare
checking what language compliance flags to pass to the C compiler... 
checking whether to enable maintainer-specific portions of Makefiles... no
checking for GTK... yes
checking for GTHUMB... configure: error: Package requirements (
	glib-2.0 		>= 2.16.0
	gthread-2.0
	gmodule-2.0
	gio-unix-2.0
	gtk+-2.0 		>= 2.16.0
	gconf-2.0 		>= 2.6.0
	unique-1.0
) were not met:

No package 'unique-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTHUMB_CFLAGS
and GTHUMB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

6. I executed make
```
make
```
Returned error:
```
make: *** No targets specified and no makefile found.  Stop.
```

7. Install
I should also execute following command, but I didn't because of errors above.
```
sudo make install
```

In step 5 there are some error of some missing packages. I should probably install some other packages, but I don't know which one?
Any idea which package should I install?
Regards

---

### Post by lemming465 on 2009-11-29
The first thing I'd try is *sudo aptitude build-depends gthumb*, which will at least pull in any missing dependencies for the stock ubuntu version.  That may or may not include 100% of what the git version needs, but it should be closer.  The error message > No package 'unique-1.0' found has to be taken seriously; restart at step 5 autogen.sh until that goes away.  You don't have a makefile because the autogen step is the one that would create it, and it's not working yet.  If the *aptitude build-depends ...* doesn't fix it, see if *sudo aptitude install libunique-dev* helps.

---

### Post by abcuser on 2009-11-30
Hi,
problem solved. Solution is:
```
sudo aptitude install libunique-dev
```
and then follow from step 5 in my first post and it works fine.
Thanks for help

---

