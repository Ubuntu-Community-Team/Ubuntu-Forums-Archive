---
title: "Network problem after upgrade from 10.04 LTS to 12.04 LTS"
date: 2012-12-21
forum: Installation &amp; Upgrades
---

### Post by DrScum on 2012-12-21
After upgrading the wlan card is not working. I followed thread [http://ubuntuforums.org/showthread.php?t=1975503](http://ubuntuforums.org/showthread.php?t=1975503) and got it to work.

The thread suggests to install firmware which I didn't have to do since it was already installed. All it took is to stop the adapter with the terminal command modprobe -r b43 and then restart it with modprobe b43. However, after rebooting I have to go through these commands again to get the adapter up. How to I fix this?

---

### Post by dino99 on 2012-12-21
network-manager have some issues, and i prefer using wicd instead.
But you also can rename some folders to get rid of some borked settings:
.gconf
.local
.gnome2
.config

after rebooting you will get fresh ones (but without your own tweaks indeed.)

---

### Post by DrScum on 2012-12-22
moved to general help section

---

