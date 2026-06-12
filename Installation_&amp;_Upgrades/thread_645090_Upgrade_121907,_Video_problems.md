---
title: "Upgrade 12/19/07, Video problems"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by joepro57 on 2007-12-19
I upgraded gutsy today 12/19.  After rebooting my resolution went from 1920 x 1200 to
800 x 600.  I have an NVIDIA GE Force 7600 GS.

I don't see any errors in /var/log/Xorg.0.log but I'm not sure what I'm looking for.

Any help would be appreciated.

joe

---

### Post by Pumalite on 2007-12-19
The update included kernel headers. Post:
blkid
cat /etc/fstab
cat /boot/grub/menu.lst
uname -a

---

