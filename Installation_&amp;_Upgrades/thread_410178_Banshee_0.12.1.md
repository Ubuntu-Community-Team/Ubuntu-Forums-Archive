---
title: "Banshee 0.12.1"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by simonsocial on 2007-04-15
Can anyone help me install this app please?

[http://banshee-project.org/Releases/0.12.1](http://banshee-project.org/Releases/0.12.1)

I have downloaded the tarball, unzipped it, the run the configure script, then when I type in **make** in the terminal I get the following message: make: *** No targets specified and no makefile found.  Stop.

---

### Post by josephus on 2007-04-15
it's probably because you have some unmet dependency.  were there any errors generated when you ran the ./configure script?

---

### Post by simonsocial on 2007-04-15
This is what the configure script printed: -

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.21... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
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
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
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
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for a BSD-compatible install... /usr/bin/install -c
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler... 
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... yes (version 2.12.4)
checking for GLIB... yes
checking for DBUS... configure: error: Package requirements (dbus-1 dbus-glib-1) were not met:

No package 'dbus-1' found
No package 'dbus-glib-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DBUS_CFLAGS
and DBUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by josephus on 2007-04-15
```
checking for DBUS... configure: error: Package requirements (dbus-1 dbus-glib-1) were not met:

No package 'dbus-1' found
No package 'dbus-glib-1' found
```

you are missing the dev files for the dbus and dbus-glib packages.  open synaptic and search for dbus.  Look for packages such as libdbus or dbus-dev, something along those lines and add those packages in. (sorry I don't know the exact names.)

Unfortunately I don't know if there is an option to output all the missing dependencies at once, therefore you'll have to keep running the configure script check for errors,going into synaptic and adding new packages until you have everything you need.  I guarantee that you are missing a lot of packages.

Is there some functionality that you are missing with the version of banshee found in the repository?

---

### Post by simonsocial on 2007-04-16
The latest version isn't in the repository only 0.11.1. I can't find a repository for the latest version. I use Banshee a lot and it crashes on a fair bit so I though I have a go with the new version to see if its any better. I will add the dependency's and see if it works then.

---

### Post by simonsocial on 2007-04-16
Ok, getting somewhere now... kinda,

I've installed loads and loads of bits but have come to a stop...

```
simon@simon-desktop:~/Downloads/Programs/libgdiplus-1.1.10$ cd /home/simon/Downloads/Programs/banshee-0.12.1
simon@simon-desktop:~/Downloads/Programs/banshee-0.12.1$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for intltool >= 0.21... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
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
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
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
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
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
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for a BSD-compatible install... /usr/bin/install -c
checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes
checking what language compliance flags to pass to the C compiler... 
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.0.0... yes (version 2.12.4)
checking for GLIB... yes
checking for DBUS... yes
checking for GTK... yes
checking for GNOMEVFS... yes
checking for MUSICBRAINZ... yes
checking for LIBNAUTILUS_BURN... yes
yes
checking for LIBNAUTILUS_BURN... yes
yes
checking for LIBNAUTILUS_BURN... yes
checking for GST... yes
checking for gst-inspect... /usr/bin/gst-inspect-0.10
checking for GStreamer 0.10 decodebin plugin... yes
checking for GStreamer 0.10 playbin plugin... yes
checking for GStreamer 0.10 cdparanoia plugin... yes
checking for GStreamer 0.10 gnomevfssink plugin... yes
checking for GStreamer 0.10 gnomevfssrc plugin... yes
checking for GStreamer 0.10 audioconvert plugin... yes
checking for GStreamer 0.10 gconfaudiosink plugin... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for MONO_MODULE... configure: error: Package requirements (mono >= 1.1.10) were not met:

No package 'mono' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONO_MODULE_CFLAGS
and MONO_MODULE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

So i've gone into Synaptic Package Manager and searched for "Mono"

When I try to install this I get the follow error: -

```
mono:
  Depends: mono-common (=1.1.17.1-1ubuntu7.1) but 1.2.3.1-1ubuntu1~dhx1 is to be installed
  Depends: mono-jit (=1.1.17.1-1ubuntu7.1) but 1.2.3.1-1ubuntu1~dhx1 is to be installed
```



Any ideas??:confused:

---

### Post by josephus on 2007-04-16
you could try going into synaptic and forcing the version that you want.  however, i'm not sure why you have that particular version of mono installed (it doesn't come from the standard edgy repository) so by downgrading you might break another package that depends on the higher version of mono.

however, that said, i would just make sure that you have the dev files associated with mono.  check if you have packages along the lines of mono-dev or libmono-dev installed.  I just upgraded to feisty so i don't know if the package names have changed in the upgrade.

---

### Post by simonsocial on 2007-04-16
Well I managed to sort... took some sorting,

First I removed all the mono items i had installed, then I had to install the original Banshee once I did this I had to add a few more installs to get the configure to work.

And now it works!! Thanks everyone!.... just need to work how to get the iPod support to work now??!

---

### Post by josephus on 2007-04-16
good job!

looks like there are two other files on the original link that you gave that you need to compile.

---

### Post by simonsocial on 2007-04-16
Yeah, i've downloaded them and compiled them but no joy. I'll look into it tomorrow and see whats up with it.

Well the new version seems to run a lot more stable, not had a crash yet. Looks a little nicer too (which always helps!)

Thanks for the help.

---

