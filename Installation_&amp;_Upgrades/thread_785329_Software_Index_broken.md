---
title: "Software Index broken"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by blue_gibbon on 2008-05-07
Dear All,
Upgrading to Hardy Heron ,I had a power surge.
Now seems like a package error.

Get the message >

Software index broken
Run synpatic manager or sudo apt-get install -f


Terminal session :

geek@geek-desktop:~$ sudo apt-get install -f
[sudo] password for geek:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
geek@geek-desktop:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0072' near line 1:
field name `=' must be followed by colon
geek@geek-desktop:~$

File 0072 :

= 2.12.0), libice6 (>= 1:1.0.0), liborbit2 (>= 1:2.14.8), libpango1.0-0 (>= 1.18.2), libpopt0 (>= 1.10), libsm6, libstartup-notification0 (>= 0.8-1), libx11-6, libxcomposite1 (>= 1:0.3-1), libxcursor1 (>> 1.1.2), libxdamage1 (>= 1:1.1), libxext6, libxfixes3 (>= 1:4.0.1), libxi6, libxinerama1, libxml2 (>= 2.6.29), libxrandr2 (>= 2:1.2.0), libxrender1
Description: Utility library for loading .desktop files - runtime files
This library is used by GNOME 2 to load the .desktop files.
Original-Maintainer: Ond&#345;ej Surý <ondrej@debian.org>

Package: libxv1
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 72
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Architecture: i386
Source: libxv
Version: 2:1.0.3-1ubuntu1
Depends: libc6 (>= 2.6), libx11-6, libxext6, x11-common
Description: X11 Video extension library
libXv provides an


How do I edit file 0072 ? Anyone please ?

      How do I edit file 0072 ? Anyone please ?

---

### Post by Pumalite on 2008-05-07
gksudo gedit /var/lib/dpkg/updates/0072
(if you have such a file)

---

### Post by blue_gibbon on 2008-05-07
I meant what should I edit in the file ? Where should I place the colon ?

---

