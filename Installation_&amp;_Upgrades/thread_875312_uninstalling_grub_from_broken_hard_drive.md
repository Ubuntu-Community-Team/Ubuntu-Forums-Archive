---
title: "uninstalling grub from broken hard drive"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by mariner8905 on 2008-07-30
My computer crashed yesterday and in the process of trying to get it to boot again i uninstalled ubuntu from my second hard drive since it did not work as it is. i have windows xp media center on my main hard drive and want that to boot up but the grub loader comes up and errors out since ubuntu is no longer there. is there any way to fix the master boot record on the hard drive when it is being looked at from an external case? i can still access the hard drive from that view.

---

### Post by Pumalite on 2008-07-30
Fix your Windows MBR with Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Or your Installation Disk

---

### Post by mariner8905 on 2008-07-30
i see what you are talking about but i dont think this will work or i dont see how it will work, i want to do the fix on the hard drive when it is an external hard drive hooked up onto another computer.

---

### Post by crwmike on 2008-07-30
Boot your XP Install CD, select Recovery Console, and run fixmbr. This will replace grub's bootloader with windows

---

