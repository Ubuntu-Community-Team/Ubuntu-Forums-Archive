---
title: "libpq-fe.h"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by jimmiy4616 on 2011-11-06
i have install all the requirements i am trying to run a program or compile it i am getting this error 
the configure command works fine but make is giving me error


vanita@vanita-Inspiron-N4050:~/sanghamithra-2.0$ sh ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... yes
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
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for PQfinish in -lpq... yes
checking postgres.h usability... no
checking postgres.h presence... no
checking for postgres.h... no
checking whether to include PostgreSQL support... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating pixmaps/Makefile
config.status: creating reports/Makefile
config.status: creating man/Makefile
config.status: creating po/Makefile
config.status: creating data/Makefile
config.status: creating glade/Makefile
config.status: creating gnome/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
vanita@vanita-Inspiron-N4050:~/sanghamithra-2.0$ make
make  all-recursive
make[1]: Entering directory `/home/vanita/sanghamithra-2.0'
Making all in src
make[2]: Entering directory `/home/vanita/sanghamithra-2.0/src'
gcc -DHAVE_CONFIG_H -I. -I.. -DPACKAGE_CONF_FILE=\""sanghamithra.conf"\" -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\" -I/usr/local/include/ -I../ -I./ -I/usr/include/libxml2 -pthread -DORBIT2=1 -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/i386-linux-gnu/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/i386-linux-gnu/gtk-2.0/include -I/usr/include/cairo -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/libpng12 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2     -Wall -Wimplicit -Wreturn-type -Wunused -Wswitch -Wcomment -Wuninitialized -Wparentheses -Wpointer-arith -g -g -O2 -MT SanghaMithra-main.o -MD -MP -MF .deps/SanghaMithra-main.Tpo -c -o SanghaMithra-main.o `test -f 'main.c' || echo './'`main.c
In file included from main.c:7:0:
osslib.h:30:22: fatal error: libpq-fe.h: No such file or directory
compilation terminated.
make[2]: *** [SanghaMithra-main.o] Error 1
make[2]: Leaving directory `/home/vanita/sanghamithra-2.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/vanita/sanghamithra-2.0'
make: *** [all] Error 2


but when i check for the file its there

---

### Post by dino99 on 2011-11-06
you have downloaded an old app:
 The latest version was released on 2009-03-18 
so this is quite understandable that actual libs (supposed you use Oneiric) are conflicting. Maybe try using Lucid (or older) or an alternative app.

[http://askubuntu.com/questions/12734/which-tool-to-use-for-home-banking](http://askubuntu.com/questions/12734/which-tool-to-use-for-home-banking)

---

