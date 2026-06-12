---
title: "Hardy/ATI Dual Monitor Operation"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by mtndog on 2008-10-24
Just installed fresh Hardy with ATI Radeon x1650 on Asus P5KC MB.  Downloaded current Linux driver for x1650 from ATI web, installed, and ran aticonfig on the terminal:

    $sudo aticonfig --initial=dual-head --screen-layout=right
    $sudo aticonfig --dtop=horizontal --overlay-on=1


After reboot, system hangs at (light) blank screen with usable mouse pointer on L-side, and a dark screen on R-side with an "X" mouse "pointer" as the mouse pointer is dragged to the R-side.  The light screen seems to be the same as the one on normal boot, just before the Gnome desktop is displayed.

Help!  How do I get a good boot with usable dual monitors?

Thanks...

---

