---
title: "Feisty killed X11."
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by insert_name_here on 2007-04-19
I upgraded to Feisty from Edgy with the alternate install CD... and upon restarting, my X11 stopped working.  It says that

*some normal stuff*
(WW) VESA: No matching Device section for instance (BusID PCI:1:0:0)
(EE) No device detected

I *might* have replaced my xorg.conf and I've checked, there are no backups.

---

### Post by muchmusic on 2007-04-19
You can run dexconf or dpkg-reconfigure xserver-xorg as root to replace with a more generic xorg .conf but this also might be the ati bug seen at [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853)

and mentioned at [http://ubuntuforums.org/showthread.php?t=413890](http://ubuntuforums.org/showthread.php?t=413890)

---

