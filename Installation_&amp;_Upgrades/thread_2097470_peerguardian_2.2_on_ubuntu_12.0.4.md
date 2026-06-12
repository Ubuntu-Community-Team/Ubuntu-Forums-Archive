---
title: "peerguardian 2.2 on ubuntu 12.0.4"
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by egandt on 2012-12-23
Spent a bunch of time fighting with this installation and packages, since I found no solution here, I thought I'd add one:

First the following builds the basic no UI model, good for a Firewall:
apt-get install debhelper dh-autoreconf po-debconf zlib1g-dev libdbus-1-dev libnetfilter-queue-dev libnfnetlink-dev p7zip-full
./configure \
    --prefix=/usr/local \
    --mandir=/usr/local/share/man \
    --datadir=/usr/local/share \
    --sysconfdir=/etc \
    --localstatedir=/var \
    --with-lsb=/lib/lsb/init-functions \
    --enable-cron \
    --enable-logrotate \
    --enable-zlib \
    --enable-lowmem \
    --without-qt4 \
    --disable-dbus \
    --with-lsb=/lib/lsb/init-functions
make


This one builds the same with all the UI goodness:
apt-get install debhelper dh-autoreconf po-debconf zlib1g-dev libdbus-1-dev libnetfilter-queue-dev libnfnetlink-dev libpolkit-qt-1-dev libqt4-dev p7zip-full
./configure \
    --prefix=/usr/local \
    --mandir=/usr/local/share/man \
    --datadir=/usr/local/share \
    --sysconfdir=/etc \
    --localstatedir=/var \
    --with-lsb=/lib/lsb/init-functions \
    --enable-cron \
    --enable-dbus \
    --enable-logrotate \
    --enable-networkmanager \
    --enable-zlib \
    --with-qt4 \
    --disable-lowmem \
    --with-lsb=/lib/lsb/init-functions
make


Notice that I used /etc,/var and put the rest of it in /usr/local.

You might need to edit /etc/init.d/pgl to look in /usr/local/lib/pgl/pglcmd.main and not the default: /usr/lib/pgl/pglcmd.main  I did on 1 system and not another.

This will get you up and running I'll leave off here as there is better documentation on configuring it.

---

### Post by jre on 2013-01-04
> **egandt said:**
> You might need to edit /etc/init.d/pgl to look in /usr/local/lib/pgl/pglcmd.main and not the default: /usr/lib/pgl/pglcmd.main  I did on 1 system and not another.

This should be handled automatically by the Makesystem. Didn't it?


Fine job, it's still on my TODO to offer additional lowmem/nodbus packages next to the full-version packages.

---

