---
title: "Problem installing grdesktop. Cannot find gtk+-2.0"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by jbernhardt on 2008-01-25
I am having trouble for installing grdesktop. I type ./configure and it cannot find gtk+-2.0. I have ubuntu 6.06

jbernhardt@jbernhardt-ws:~/grdesktop-0.23$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for an ANSI C-conforming const... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for strerror in -lcposix... no
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking for string.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/files.h usability... no
checking sys/files.h presence... no
checking for sys/files.h... no
checking sys/params.h usability... no
checking sys/params.h presence... no
checking for sys/params.h... no
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  de fr es
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0... configure: error: cannot find GTK+ 2.0!

---

### Post by taurus on 2008-01-25
Fire up synaptic, System -> Administration -> Synaptic Package Manager, and Search for libgtk.  Install the -dev package first and then run that command to build grdesktop again.

---

