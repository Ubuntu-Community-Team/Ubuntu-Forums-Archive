---
title: "SiS 771/671 driver installation PROBLEM"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by ncvaldez on 2009-12-19
[B][FONT=Arial][SIZE=3]SiS 771/671 driver installation PROBLEM
I recently upgrade to 9.10 (and I'm new to Linux) and found the old settings(hence the driver) for the display of my laptop gone...
I tried to get a hold of a driver (from [http://ncc-1701a.homelinux.net/~linux-sis/downloads/xorg-driver-sis671_0.9.tar.gz]("http://ncc-1701a.homelinux.net/%7Elinux-sis/downloads/xorg-driver-sis671_0.9.tar.gz") ) and tried to install it but I have an itsy bitsy problem because as I install it this shows up(after writing ./autogen.sh --prefix=/usr):[/SIZE][/FONT][/B][INDENT][SIZE=3]autoreconf: Entering directory `.'[/SIZE]
[SIZE=3] autoreconf: configure.ac: not using Gettext[/SIZE]
[SIZE=3] autoreconf: running: aclocal [/SIZE]
[SIZE=3] autoreconf: configure.ac: tracing[/SIZE]
[SIZE=3] autoreconf: running: libtoolize --install --copy[/SIZE]
[SIZE=3] libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and[/SIZE]
[SIZE=3] libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.[/SIZE]
[SIZE=3] libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.[/SIZE]
[SIZE=3] autoreconf: running: /usr/bin/autoconf[/SIZE]
[SIZE=3] autoreconf: running: /usr/bin/autoheader[/SIZE]
[SIZE=3] autoreconf: running: automake --add-missing --copy --no-force[/SIZE]
[SIZE=3] Makefile.am:24: BUILD_LINUXDOC does not appear in AM_CONDITIONAL[/SIZE]
[SIZE=3] autoreconf: automake failed with exit status: 1[/SIZE]
[/INDENT][SIZE=3] 
**I think this has something to do with packages needed to be installed but I have no idea what the packages are (or if I'm wrong... I don't know then what is going on :confused: ). Can someone help me please?**
[/SIZE]

---

### Post by Rhodderz on 2010-01-16
Hi i have the same prob and wondering if you had any news on it. 
cheer

ps, sis is horrible the drivers are free on wondows why not on linux :(

---

### Post by mascygp on 2010-01-30
on Debian I resolved installing **xutils** and **xutils-dev** packages.
Good Fun

---

