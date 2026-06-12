---
title: "Remove windows boot loader"
date: 2014-11-23
forum: Installation &amp; Upgrades
---

### Post by veganrailpunk on 2014-11-23
Hi

When I set up my dual boot of Windows 7 and Lubuntu about a year and a half ago I was advised to keep the Windows boot loader on the MBR. When I boot up I first load the windows bootloader which has grub2 as default, it then goes into grub2 which has Lubuntu as default. I was hoping to speed up boot time by going straight into grub2. I still want to be able to access Windows occasionally.

Basically I want to put grub2 on the MBR without messing up my system and still being able to boot into all my OSes.

I have looked on the forums at other similar queries but these have seemed to be regarding dual installs using wubi. My installation is on separate partitions.

Any help would be very gratefully received.

Thanks Pete

---

### Post by veganrailpunk on 2014-11-23
Ok, solved it myself

just did:
sudo grub-install /dev/sda
sudo update-grub

and everything works fine.

---

