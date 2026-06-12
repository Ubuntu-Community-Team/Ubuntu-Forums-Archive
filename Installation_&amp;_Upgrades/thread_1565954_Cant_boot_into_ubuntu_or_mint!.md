---
title: "Cant boot into ubuntu or mint!"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by rab2140 on 2010-09-01
Hi all, i have no idea whats going on but, i try to install unbuntu on my 80gb hdd and the install goes fine then i reboot and i just boot back into windows ! the grub boot loader doesnt even load, then i go to unistall via windows and it says there is an error and that the boot bath cant be found. i tried installing another os a few days ago and i partioned the hdd into 3 seperate one but then formatted back to ntfs and i now i cant install any linux o's! have i done something to the mbr on that hdd?

---

### Post by quixote on 2010-09-04
Are you installing ubuntu from within Windows (i.e. the wubi version)?  Or is this an ordinary dual boot install?

If the latter, there's a point during installation where grub asks, rather cryptically, whether you want it on the MBR or a partition.  You actually need it on the MBR.  

(MBR contains the bootloader which is like a mini-operating system that points the machine to the right partition to load the rest of the OS.  Windows will only point to Windows, but grub will, after the first boot and an update command, point to all OSes on your drives.)

Linux OSes can only run from linux-formatted partitions.  For us, in practical terms, that means ext3 or ext4, although there are lots of others.  Ntfs and vfat are Windows formats, and hpfs is Mac format, none of which will support a Linux OS.  Linux can read data on those formats though.

---

