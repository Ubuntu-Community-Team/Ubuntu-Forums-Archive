---
title: "rTorrent, problem with installting libtorrent."
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by brange on 2007-01-05
Hello.

I tried to install rTorrent with this guide:
[http://libtorrent.rakshasa.no/wiki/Install](http://libtorrent.rakshasa.no/wiki/Install)
but when I came to ./autogen.sh I got this message:
aclocal...
aclocal not found

I googled a bit and found out that aclocal is a part of automake, so I run:
apt-get install automake
then
./autogen.sh again
And now I got this messeage instead.
aclocal...
aclocal: configure.ac: 21: macro `AM_DISABLE_STATIC' not found in library
aclocal: configure.ac: 22: macro `AM_PROG_LIBTOOL' not found in library
autoheader...
autoheader: error: AC_CONFIG_HEADERS not found in configure.ac
libtoolize... libtoolize nor glibtoolize not found

now I don't know what to do, someone has any ideas?

---

### Post by an.echte.trilingue on 2007-01-05
Is there a reason you don't want to apt-get install rtorrent?

---

### Post by brange on 2007-01-05
Yes, the version you get when you apt-get it is pretty old and doesn't support encrypted traffic.

---

### Post by an.echte.trilingue on 2007-01-05
I've been looking around and it seems that libtoolize is part of X11... which seems strange for an ncurses based program.  Give me a couple minutes to look at this...

---

### Post by an.echte.trilingue on 2007-01-05
libtoolize is part of the libtool package.  You should probably also install build-essential if you haven't yet.

---

### Post by brange on 2007-01-05
Yeajh, apt-get install libtool did the job!:)

Thanks alot

---

