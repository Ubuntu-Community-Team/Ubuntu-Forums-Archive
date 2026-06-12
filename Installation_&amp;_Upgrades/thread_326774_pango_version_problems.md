---
title: "pango version problems"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by grizzlysmit on 2006-12-28
](*,)  I tryed to install gobby and I get the following error 
> gobby:
  Depends: libpango1.0-0 (>=1.12.3) but 1.12.2-0ubuntu3 is to be installed

where do I get a higher version of pango this isn't the first time I needed this but synaptic cannot find it for me I'm using ubuntu 6.06

---

### Post by bapoumba on 2006-12-28
I have gobby up and running :

```
~ $ aptitude show gobby
E: /home/isabella/.aptitude/config - Unable to open %s for writing (13 Permission denied)
Package: gobby
State: installed
Automatically installed: no
Version: 0.4.1-1ubuntu1
Priority: optional
Section: universe/net
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 2089k
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.12.1),
         libavahi-compat-howl0 (>= 0.6.0), libc6 (>= 2.4-1), libcairo2 (>=
         1.2.4), libcairomm-1.0-1, libfontconfig1 (>= 2.3.0), libgcc1 (>=
         1:4.1.1-12), libgconf2-4 (>= 2.13.5), libglib2.0-0 (>= 2.12.0),
         libglibmm-2.4-1c2a, libgnomeprint2.2-0 (>= 2.12.1), libgnomevfs2-0 (>=
         2.15.90), libgnutls13 (>= 1.4.0-0), libgtk2.0-0 (>= 2.10.3),
         libgtkmm-2.4-1c2a, libgtksourceview1.0-0 (>= 1.7.2), libnet6-1.3-0 (>=
         1:1.3.1-1), libobby-0.4-0 (>= 0.4.1-1), liborbit2 (>= 1:2.14.1),
         **libpango1.0-0 (>= 1.14.3)**, libsigc++-2.0-0c2a (>= 2.0.2), libstdc++6
         (>= 4.1.1-12), libx11-6, libxcursor1 (> 1.1.2), libxext6, libxfixes3,
         libxi6, libxinerama1, libxml++2.6c2a, libxml2 (>= 2.6.26), libxrandr2,
         libxrender1, zlib1g (>= 1:1.2.1)
Suggests: avahi-daemon

```

```
Package: libpango1.0-0
State: installed
Automatically installed: no
Version: 1.14.5-0ubuntu1
Priority: optional
Section: libs

```

What is the output to **cat /etc/apt/sources.lis**t ?

---

