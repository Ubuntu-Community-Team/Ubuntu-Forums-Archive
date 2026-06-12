---
title: "X trouble after upgrade"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by kao on 2005-11-15
I've had upgrade my X (breezy/hoary) rev. 6x to rev. 77 from breezy repository. So it's lacked auto loading with /etc/init.d/gdm. Error log in /var/log/Xorg.0.log is empty. Startx is disfunctional too (prints "xinit: server error")
I can start X manually only.

PS what difference between X and Xorg binaries

---

### Post by chris_andrew on 2005-11-15
Have you tried to run:

dpkg-reconfigure xserver-xorg (I think)?

Chris.

---

### Post by kao on 2005-11-15
[QUOTE=chris_andrew]Have you tried to run:

dpkg-reconfigure xserver-xorg (I think)?

Chris.[/QUOTE]

that package is not necessary now, so it's not installed
thanks for reply, but problem is fixed
just ln -sf /usr/X11R6/bin/Xorg /usr/X11R6/bin/X 
so source of troubles was strange disfunctional binary X (from xserver-common)

---

