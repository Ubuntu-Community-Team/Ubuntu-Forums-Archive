---
title: "Problems Installing/Upgrading"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by GlitchKing on 2011-02-02
I'm using Ubuntu 10.10. I'm starting to get a little fed up with the way it works. You can never install anything without having errors. Then when you go to install the fixes for the errors all you end up with is MORE ERRORS! My nerves can't handle this OS anymore. I'm willing to give it ONE MORE CHANCE! I need help, please.

Trying to install empathy 2.91.6

Getting the following error.

```
brandon@brandon-ubuntu:~$ cd /home/brandon/Downloads/empathy-2.91.6/
brandon@brandon-ubuntu:~/Downloads/empathy-2.91.6$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.0.0... yes (version 2.26.0)
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
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
checking gnome-doc-utils >= 0.17.3... yes
checking for dbus-binding-tool... no
checking for pkg-config... (cached) /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for xsltproc... xsltproc
checking for a Python interpreter with version >= 2.3... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/dist-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/dist-packages
checking for VALGRIND... no
checking for valgrind... no
checking to see if compiler understands -Wall... yes
checking to see if compiler understands -Werror... yes
checking to see if compiler understands -Wextra... yes
checking to see if compiler understands -Wno-missing-field-initializers... yes
checking to see if compiler understands -Wno-unused-parameter... yes
checking to see if compiler understands -Wdeclaration-after-statement... yes
checking to see if compiler understands -Wshadow... yes
checking to see if compiler understands -Wmissing-prototypes... yes
checking to see if compiler understands -Wmissing-declarations... yes
checking for EMPATHY... no
configure: error: Package requirements (
   dbus-glib-1
   farsight2-0.10
   folks >= 0.3.4
   folks-telepathy >= 0.3.4
   gio-2.0 >= 2.27.2
   gio-unix-2.0 >= 2.27.2
   gnome-keyring-1 >= 2.26.0
   gnutls >= 2.8.5
   gmodule-export-2.0
   gobject-2.0
   gsettings-desktop-schemas
   gstreamer-0.10
   gstreamer-interfaces-0.10
   libxml-2.0
   telepathy-farsight >= 0.0.14
   telepathy-glib >= 0.13.11
   telepathy-logger-0.1 >= 0.1.5
   x11
   gtk+-3.0 >= 2.99.0
   libcanberra-gtk3 >= 0.25
   libnotify >= 0.7.0
   gcr-3 >= 2.91.4
) were not met:

No package 'dbus-glib-1' found
No package 'farsight2-0.10' found
No package 'folks' found
No package 'folks-telepathy' found
Requested 'gio-2.0 >= 2.27.2' but version of GIO is 2.26.0
Requested 'gio-unix-2.0 >= 2.27.2' but version of GIO unix specific APIs is 2.26.0
No package 'gnome-keyring-1' found
No package 'gsettings-desktop-schemas' found
No package 'gstreamer-0.10' found
No package 'gstreamer-interfaces-0.10' found
No package 'libxml-2.0' found
No package 'telepathy-farsight' found
No package 'telepathy-glib' found
No package 'telepathy-logger-0.1' found
No package 'gtk+-3.0' found
No package 'libcanberra-gtk3' found
No package 'libnotify' found
No package 'gcr-3' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EMPATHY_CFLAGS
and EMPATHY_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
brandon@brandon-ubuntu:~/Downloads/empathy-2.91.6$ 
```

I used synatics to find the packages and most are already installed. I also found some that weren't and installed them and it still shows as not found.

HELPPPPPP!

Thanks.):P

---

### Post by Larrxi on 2011-02-02
Did you install the dev-packages for the packages not found? For example folks-dev. You may need to enable the source repository in synaptics.

---

### Post by sikander3786 on 2011-02-02
Why are you installing empathy from source? If that is not absolutely necessary, you can simply install empathy from the repositories.

```
sudo apt-get update && sudo apt-get install empathy
```

For package dependency problems,

```
sudo dpkg --configure -a
sudo apt-get install -f
```

---

