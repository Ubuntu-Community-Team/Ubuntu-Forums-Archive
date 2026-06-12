---
title: "Remove Ubuntu"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by sparkguitar05 on 2008-06-16
How do I completely remove Ubuntu from my computer?

I know how to delete the partitions, so I guess my real question is how to get rid of the GRUB and bring back the Windows XP bootloader.

I currently have Windows XP and Hardy installed on the same hard drive in different partitions.  I want to remove Hardy and just have XP.

---

### Post by Pumalite on 2008-06-16
Erase the Ubuntu partition and fix your Windows MBR with Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by abantu_IV on 2008-06-18
> **sparkguitar05 said:**
> How do I completely remove Ubuntu from my computer?

I know how to delete the partitions, so I guess my real question is how to get rid of the GRUB and bring back the Windows XP bootloader.

I currently have Windows XP and Hardy installed on the same hard drive in different partitions.  I want to remove Hardy and just have XP.
Hi. I would like to remove the OpenSUSE in my laptop (its not working anyway). How do i go about deleting partitions? And will the space be available after that for other uses? My laptop runs Vista. Please help. Thanks.

---

### Post by Pumalite on 2008-06-18
Post:
sudo fdisk -lu
And a screenshot of Gparted showing the offending partitions.

---

