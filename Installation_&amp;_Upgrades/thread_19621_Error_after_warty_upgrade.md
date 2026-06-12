---
title: "Error after warty upgrade"
date: 2005-03-12
forum: Installation &amp; Upgrades
---

### Post by joplass on 2005-03-12
I did “Mark All Upgrades”, “Apply” from Synaptic, and I reboot the box.  Then this error came up.  I really don't know where to report it or if there is anything I have to do.  I closed it and the machine runs fine as far as I can tell.

Error activating XKB configuration.
Probably internal X server problem.

X server version data:
The Xfree86 Project, Inc
40300001
You are using Xfree 4.3.0
There are known problems with complex XKB configurations.
Try using simpler configuration or a newer version of the Xfree software.
if you report this situation as a bug, please include:
-The result of xprop -root | grep XKB
-The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/xkb

---

