---
title: "Help on replacing a linux distribution with ubuntu"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by remerico on 2007-06-11
Hello,

I currently have a dual-boot setup on my system consisting of Windows XP SP2 and Slackware 11. My partition is laid out like this:


29.78 GB [NTFS] - Windows XP Partition
8.27 GB  [ext3] - Slackware 11 Partition
1.00 GB  [swap] - Linux swap
193.82GB   [NTFS] - Files/Data Partition

I have Lilo installed in the MBR that lets me choose what operating system to boot at startup.

My problem is how do I replace Slackware with Ubuntu without rendering Windows unbootable? Would Ubuntu still be able to detect my Windows partition even though Lilo is already installed in the MBR?

I've just downloaded Ubuntu 7.04 and I want to try it out. :D

Thanks. :)

---

### Post by H3g3m0n on 2007-06-11
Just boot with the LiveCD and you should be able to install over the Slackware partitions with the installer. Ubuntu will install Grub and should automatically detect you windows for you. Otherwise you need to edit /etc/grub/menu.lst

---

### Post by remerico on 2007-06-11
Hi,

I've just installed Ubuntu 7.04 and it detected Windows without any problems. Thank you. :)

Ubuntu rocks. :D

---

