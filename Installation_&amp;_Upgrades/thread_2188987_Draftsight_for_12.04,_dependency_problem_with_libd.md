---
title: "Draftsight for 12.04, dependency problem with libdirectfb-extra,"
date: 2013-11-20
forum: Installation &amp; Upgrades
---

### Post by psyclone on 2013-11-20
Hi all,
I'm trying to run draftsight on a 64bit system. When I try to run the program from terminal there's a dependency problem with  libdirectfb-extra. As follows:

e-desktop@edesktop:~$ sudo dpkg -i --force-architecture draftSight.
debdpkg: regarding draftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
dassault-systemes-draftsight:i386 pre-depends on libdirectfb-extra (>= 1.2.7-2)
dpkg: error processing draftSight.deb (--install):
pre-dependency problem - not installing dassault-systemes-draftsight:i386
Errors were encountered while processing:
draftSight.deb
e-desktop@edesktop:~$

I've read many draftsight posts, but non of there solutions have helped (the ones I've read).

---

### Post by psyclone on 2013-11-20
I've solved the problem through removing and re-installing [COLOR=#000000]libdirectfb-extra.


[/COLOR]

---

### Post by jp734 on 2013-12-21
installing** libcanberra-gtk-module:i386** and **libcanberra-gtk0:i386** did it for me.

---

