---
title: "Raid 5 on lvm"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by jimx on 2006-12-09
Hello,
I'm trying to install Ubuntu Server 6.10 Edgy Eft on a raid 5 array on LVM with 4 disks 4x250GB.I have done a boot partition on md0 out of the lvm and the rest space on md1 with mount points for root,swap,home,opt in the lvm,so the output is like that:

/boot 200MB on md0
/root 10GB on md1
/home 20GB on md1
/swap  4GB on md1
/opt on md1 the rest space of the disks.

Everything goes well but when it comes to install the boot loader
it chooses lilo but stops before it installs it with an exit error:
Running "/sbin/lilo" failed with error code "1".
I tried again and put grub as the boot loader but grub freezes at 50% of the installation and i have to reset the PC.

My hardware is:
MSI P965 Platinum,Core 2 Duo 2.13Ghz,2GB Ram,4X250GB WD sata2

---

