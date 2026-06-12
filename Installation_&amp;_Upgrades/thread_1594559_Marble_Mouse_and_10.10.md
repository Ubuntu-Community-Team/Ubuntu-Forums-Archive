---
title: "Marble Mouse and 10.10"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by dld on 2010-10-12
I have 10.10 up and running, and am making those little "adjustments" that are special to me.  I am stuck with Marble Mouse scrolling (again).  I have all the old code from 10.04.
/etc/hal/fdi/policy/marblemouse.fdi
/usr/lib/X11/xorg.conf.d/20-marblemouse.conf
But no scrolling.   All the articles in the Forum are old.  Something must have changed in 10.10.  Anyone know what and how to get back to scrolling the way my fingers automatically work?


Copying /usr/lib/X11/xorg.conf.d/20-marblemouse.conf  to /etc/X11/xorg.conf
restored vertical and horizontal scrolling.

This year for 11.04 I had to copy xorg.conf to /usr/share/X11/xorg.conf.d/50-marblemouse.conf.  Every Ubuntu upgrade
is a challenge!

---

### Post by geokker on 2010-11-17
I'm in the same boat. Do you mind posting your conf? I didn't have /usr/lib/X11/xorg.conf.d/ on my old 10.04 (64bit) system. I've now moved to a 32bit chip.

---

