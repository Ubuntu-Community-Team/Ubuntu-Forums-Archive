---
title: "Grub error 22, cant boot XP or Debian"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by dzuari on 2008-01-13
i just installed debian-40r2-i386-netinst.iso onto a portable hard drive but when i try to boot it up through grub it gives me the error 22 and the same thing happens when i try to boot XP, im currently running off my 2G flash drive with puppy linux. Iv deleted the debian partition through puppy and i dont have the XP cd so i cant boot in recovery mod.

---

### Post by john_spiral on 2008-01-13
post the results from the below command:

sudo fdisk -l

and the contents of /boot/grub/menu.lst

---

### Post by Pumalite on 2008-01-13
Probably stage1 of Grub is in your external and your stage2 in your internal or viseversa. Install again. The best way to avoid this in a Desktop is to disconnect all internal drives during the installation. You can probably use Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by dzuari on 2008-01-13
i disengaged my internal HD and installed Ubuntu7.10desktop to my USB HD, im updating ubuntu right now but when its done i'll try to boot to XP and post wat happens

---

