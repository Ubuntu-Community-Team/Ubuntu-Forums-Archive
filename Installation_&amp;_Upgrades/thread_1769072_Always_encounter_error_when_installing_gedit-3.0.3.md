---
title: "Always encounter error when installing gedit-3.0.3"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by 5tuden7 on 2011-05-27
Hi,

my system is newly installed 10.10 ubuntu with all updates patched.

I want to install gedit 3.0.3 and I just followed all steps in the README:

> 
Installation
============

gedit requires GTK+-3.0.x and GtkSourceView 3.0.x and libpeas 1.0.x libraries.
PyGobject 2.28.x and gobject-introspection 0.9.0 are required to enable python
plugins support.

Simple install procedure:

  % gzip -cd gedit-3.0.3.tar.gz | tar xvf -     # unpack the sources
  % cd gedit-3.0.3                # change to the toplevel directory
  % ./configure                    # run the `configure' script
  % make                    # build gedit
  [ Become root if necessary ]
  % make install                # install gedit

and after I run ./configure, the error came up and here is what it says:

> 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether make sets $(MAKE)... (cached) yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for gcc... gcc
checking whether we are using the GNU Objective C compiler... no
checking whether gcc accepts -g... no
checking dependency style of gcc... gcc3
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/dist-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/dist-packages
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
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
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
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
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gtkdoc-check... no
checking for gtkdoc-rebase... no
checking for gtkdoc-mkpdf... no
checking whether to build gtk-doc documentation... no
checking for sigaction... yes
checking for floor in -lm... yes
checking for Win32 platform... no
checking for native Win32... no
checking for Mac OS X platform... no
checking for native Mac OS X... no
checking whether NLS is requested... yes
checking for intltool >= 0.40.0... 0.41.1 found
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
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... (cached) /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for LIBSOUP... no
checking for ENCHANT... no
configure: error: Enchant library not found or too old. Use --disable-spell to build without spell plugin.well I just try ./configure --disable-spell afterwards and still encounter an error like this:

> 
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether make sets $(MAKE)... (cached) yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for gcc... gcc
checking whether we are using the GNU Objective C compiler... no
checking whether gcc accepts -g... no
checking dependency style of gcc... gcc3
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/dist-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/dist-packages
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
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
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
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
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for gtkdoc-check... no
checking for gtkdoc-rebase... no
checking for gtkdoc-mkpdf... no
checking whether to build gtk-doc documentation... no
checking for sigaction... yes
checking for floor in -lm... yes
checking for Win32 platform... no
checking for native Win32... no
checking for Mac OS X platform... no
checking for native Mac OS X... no
checking whether NLS is requested... yes
checking for intltool >= 0.40.0... 0.41.1 found
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
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for msgmerge... (cached) /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for LIBSOUP... no
checking for GEDIT... no
configure: error: Package requirements (
    libxml-2.0 >= 2.5.0
    glib-2.0 >= 2.28.0
    gthread-2.0 >= 2.13.0
    gio-2.0 >= 2.26.0
    gtk+-3.0 >= 3.0.0
    gtksourceview-3.0 >= 3.0.0
    libpeas-1.0 >= 0.7.3
    libpeas-gtk-1.0 >= 0.7.3
    gsettings-desktop-schemas
) were not met:

No package 'libxml-2.0' found
No package 'glib-2.0' found
No package 'gthread-2.0' found
No package 'gio-2.0' found
No package 'gtk+-3.0' found
No package 'gtksourceview-3.0' found
No package 'libpeas-1.0' found
No package 'libpeas-gtk-1.0' found
No package 'gsettings-desktop-schemas' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GEDIT_CFLAGS
and GEDIT_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
I'm really really pleased if anyone can tell me how to solve this problem?? Very urgent.

Thanks

---

### Post by dFlyer on 2011-05-27
If your going to compile from source you will need to install the missing libs.

---

### Post by 5tuden7 on 2011-05-27
Thank you!

but how can I install the missing libs?

---

