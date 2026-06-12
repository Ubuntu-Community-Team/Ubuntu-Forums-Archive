---
title: "Trouble installing ncurses"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by Dr.Lightning on 2011-02-23
I'm new to *admin* on Linux.

I'm trying to install ncurses on Ubuntu 10.04.  I downloaded ncurses_5.7+20090803.orig.tar.gz from [http://packages.ubuntu.com/source/lucid/ncurses](http://packages.ubuntu.com/source/lucid/ncurses), unzipped it into /opt/ncurses-5.7+20090803, ran "./configure" and then "make".

Make output tons of stuff, but ended with:

[INDENT]cd ../objects;   -I../c++ -I../include -I. -DHAVE_CONFIG_H  -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64  -DNDEBUG -I. -I../include  -c ../c++/cursesf.cc
/bin/sh: -I../c++: not found
make[1]: *** [../objects/cursesf.o] Error 127
make[1]: Leaving directory `/opt/ncurses-5.7+20090803/c++'
make: *** [all] Error 2[/INDENT]

Note that the folder /opt/ncurses-5.7+20090803/c++ exists.
/opt/ncurses-5.7+20090803/objects/cursesf.o does NOT exist.
/opt/ncurses-5.7+20090803/c++/cursesf.cc and .h exist.
/opt/ncurses-5.7+20090803/c++/cursesf.app exists.
/opt/ncurses-5.7+20090803/c++/internal.h exists.

Please hold my hand and tell me what's wrong and what to do.

Thanks very much.

BTW, more output, starting from higher up:

[INDENT]gcc -O2 --param max-inline-insns-single=1200  -o xmas ../objects/xmas.o  -I../test -I. -DHAVE_CONFIG_H  -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64  -DNDEBUG -I. -I../include -O2 --param max-inline-insns-single=1200  `echo "-static -L../lib -lform -lmenu -lpanel -lncurses  -dynamic  " | sed -e 's/-lform.*-lpanel[^ ]*//'` -lutil  -lm
make[1]: Leaving directory `/opt/ncurses-5.7+20090803/test'
cd misc && make DESTDIR="" all
make[1]: Entering directory `/opt/ncurses-5.7+20090803/misc'
WHICH_XTERM=xterm-new \
	ticdir=/usr/share/terminfo \
	/bin/sh ./gen_edit.sh >run_tic.sed
echo '** adjusting tabset paths'
** adjusting tabset paths
sed -f run_tic.sed ../misc/terminfo.src >terminfo.tmp
make[1]: Leaving directory `/opt/ncurses-5.7+20090803/misc'
cd c++ && make DESTDIR="" all
make[1]: Entering directory `/opt/ncurses-5.7+20090803/c++'
cp ./etip.h.in etip.h
sh ./edit_cfg.sh ../include/ncurses_cfg.h etip.h
substituting autoconf'd values from ../include/ncurses_cfg.h into etip.h
... CPP_HAS_PARAM_INIT 0
... CPP_HAS_STATIC_CAST 0
... ETIP_NEEDS_MATH_EXCEPTION 0
... ETIP_NEEDS_MATH_H 0
... HAVE_BUILTIN_H 0
... HAVE_GPP_BUILTIN_H 0
... HAVE_GXX_BUILTIN_H 0
... HAVE_IOSTREAM 0
... HAVE_TYPEINFO 0
... HAVE_VALUES_H 0
... IOSTREAM_NAMESPACE 0
cd ../objects;   -I../c++ -I../include -I. -DHAVE_CONFIG_H  -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64  -DNDEBUG -I. -I../include  -c ../c++/cursesf.cc
/bin/sh: -I../c++: not found
make[1]: *** [../objects/cursesf.o] Error 127
make[1]: Leaving directory `/opt/ncurses-5.7+20090803/c++'
make: *** [all] Error 2[/INDENT]

---

### Post by itcotbtoemik on 2011-02-24
You're missing a C++ compiler, e.g., "g++". That's noted in the configure script output.

---

### Post by itcotbtoemik on 2011-02-24
Ubuntu has a package for ncurses, compiling your own isn't what newbie admins generally do. :)

---

