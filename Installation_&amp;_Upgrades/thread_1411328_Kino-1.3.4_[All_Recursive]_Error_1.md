---
title: "Kino-1.3.4 [All Recursive] Error 1"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by dcbullock on 2010-02-19
Fedora, trying to make/install kino-1.3.4, the ./configure goes alright, but near the end of the make process I get this.........


../../libtool: line 984: g++: command not found
make[4]: *** [entry_points.lo] Error 1
make[4]: Leaving directory `/home/dcbullock/Desktop/kino-1.3.4/src/timfx'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/dcbullock/Desktop/kino-1.3.4/src/timfx'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dcbullock/Desktop/kino-1.3.4/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dcbullock/Desktop/kino-1.3.4'
make: *** [all] Error 2


Seems to be where things are going wrong, any ideas?.... Thanks guys.

---

### Post by dcbullock on 2010-02-19
[CENTER]**_UPDATE_**
[/CENTER]
[LEFT]Got past the make stage and now similar error, during installation....
[/LEFT]


libtool: install: /usr/bin/install -c .libs/libtimfx.so /usr/local/lib/kino-gtk2/libtimfx.so
/usr/bin/install: cannot stat `.libs/libtimfx.so': No such file or directory
make[4]: *** [install-libLTLIBRARIES] Error 1
make[4]: Leaving directory `/home/dcbullock/Desktop/kino-1.3.4/src/timfx'
make[3]: *** [install-am] Error 2
make[3]: Leaving directory `/home/dcbullock/Desktop/kino-1.3.4/src/timfx'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/dcbullock/Desktop/kino-1.3.4/src/timfx'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/dcbullock/Desktop/kino-1.3.4/src'
make: *** [install-recursive] Error 1

Think im missing somthing to do with libs/libtimfx.so'?

---

