---
title: "Empathy installation error"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by fangslayer on 2010-03-09
First off, I would like to tell everyone that I am quite new to Ubuntu and Linux in general, I've just been using it for a week and find it awesome =D

However, with the version of empathy that came with Ubuntu, 2.28.1.1 there is a problem where I cannot voice call, video call or invite people to the conversation because the option is whited out. When I searched around, I found that this problem was fixed in a newer version of empathy. Thus, I planned to install 2.29.2

The problem is after I follow cd to the directory and put in ./autogen.sh I get the following code:

```

/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... found 2.64
checking for automake >= 1.9...
  testing automake-1.11... found 1.11
checking for libtool >= 1.5...
  testing libtoolize... found 2.2.6
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.22.3
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
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.ac
Running libtoolize...
libtoolize: putting auxiliary files in AC_CONFIG_AUX_DIR, `.'.
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
You should update your 'aclocal.m4' by running aclocal.
Putting files in AC_CONFIG_MACRO_DIR, 'm4'.
Running aclocal-1.11...
Running autoconf2.50...
Running autoheader2.50...
Running automake-1.11...
Running ./configure ...
checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
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
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
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
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.0.0... yes (version 2.22.3)
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking whether NLS is requested... yes
checking for intltool >= 0.35.0... 0.41.0 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.0
checking for XML::Parser... ok
checking gnome-doc-utils >= 0.17.3... yes
./configure: line 13157: IDT_COMPILE_WARNINGS: command not found
checking for dbus-binding-tool... /usr/bin/dbus-binding-tool
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
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
checking for LIBEMPATHY... yes
checking for LIBEMPATHYGTK... yes
checking for EMPATHY... yes
checking for LIBNOTIFY... yes
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
checking for NETWORK_MANAGER... no
checking for WEBKIT... no
checking for ENCHANT... no
checking for LIBCHAMPLAIN... no
checking for GEOCLUE... no
checking for NST... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating data/Makefile
config.status: creating data/empathy.desktop.in
config.status: creating data/icons/Makefile
config.status: creating extensions/Makefile
config.status: creating po/Makefile.in
config.status: creating libempathy/Makefile
config.status: creating libempathy-gtk/Makefile
config.status: creating src/Makefile
config.status: creating nautilus-sendto-plugin/Makefile
config.status: creating help/Makefile
config.status: creating tests/Makefile
config.status: creating tests/interactive/Makefile
config.status: creating tests/xml/Makefile
config.status: creating tools/Makefile
config.status: creating shave
config.status: creating shave-libtool
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

Configure summary:

	Compiler....................:  gcc
	Compiler Flags..............:  -g -O2 -Wall -Wdeclaration-after-statement -Wshadow -Wmissing-prototypes -Wmissing-declarations
	Prefix......................:  /usr/local
	Shaved build................:  no
	Coding style checks.........:  yes

    Features:
	Spell checking (enchant)....:  no
	Display maps (libchamplain).:  no
	Location awareness (Geoclue):  no
	Adium themes (Webkit).......:  no
	Moblin widgets .............:  no

    Connectivity:
	NetworkManager integration..:  no
	ConnMan integration.........:  

    Extras:
	Nautilus-sendto plugin......:  no

Now type `make' to compile Empathy


```

Now after that if I put in make it just spits out a bunch of errors.

If anyone knows how to fix this, it would be much appreciated.

---

### Post by MelDJ on 2010-03-10
it would be easier if you add their daily build repo to your sources and install from there.
in terminal:
```
sudo add-apt-repository ppa:amoog/empathy-daily
```[B]

then 

[/B]```
**sudo apt-get update
```**[B]

and finally 

[/B]```
**sudo apt-get upgrade
```**

---

### Post by fangslayer on 2010-03-10
It works =D

Thanks for the help. For future reference, may I ask how you find the repositories for any ubuntu application so I can upgrade it through terminal as opposed to compiling sources? 

Thanks again

---

### Post by MelDJ on 2010-03-18
> **fangslayer said:**
> It works =D

Thanks for the help. For future reference, may I ask how you find the repositories for any ubuntu application so I can upgrade it through terminal as opposed to compiling sources? 

Thanks again


go to google and search for:
```
yourappsname launchpad
```

---

