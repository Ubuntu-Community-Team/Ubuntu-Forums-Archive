---
title: "Dual Boot goes straight to windows"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by beninpoland on 2007-12-06
Hi

I followed the guide here:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

to install Ubuntu alongside Windows XP.

I set up my partitions as follows:

C: is 10 GB, NTFS where windows XP is installed
D: is 28 GB of FAT-32 for my shared data. I mounted this as "share" during the ubuntu installation.
I set up 32 GB of ext3 and mounted it as "/" during the ubuntu installlation
I set up 2GB of swap also.

When I reboot the PC now it boots straight into Windows XP, and doesn't give me a choice of operating systems.

I thought that Grub should kick in and manage this? What have I done wrong??

Thanks.

Ben

---

### Post by forestpixie on 2007-12-06
apart from installing xp - not much :)

xp rewrites it's bootloader - you need to reinstall grub - you can do it from the livecd - 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

or you can download, burn as an iso and boot with supergrub
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by MQMike on 2007-12-06
Here's another one that will fix this for you and guide you to dual-boot harmony with your XP:

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(aka Qqmike)

---

### Post by beninpoland on 2007-12-06
Hi

Thanks for your quick replies. I had a look at trying to fix it with grub, but am concerned that Ubuntu isn't happy with my hardware RAID - I have two hard disks which are mirrored.  Windows sees only "one disk" as expected, but Ubuntu sees the underlying disks:

root@ubuntu:~# fdisk -l
omitting empty partition (6)

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ade8ade

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1305    10482381    7  HPFS/NTFS
/dev/sda2            1306        5714    35415292+   f  W95 Ext'd (LBA)
/dev/sda3            5715        9729    32250487+  83  Linux
/dev/sda5            1306        5536    33985476    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ade8ade

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1305    10482381    7  HPFS/NTFS
/dev/sdb2            1306        5714    35415292+   f  W95 Ext'd (LBA)
/dev/sdb3            5715        9468    30154005   83  Linux
/dev/sdb4            9469        9729     2096482+  82  Linux swap / Solaris
/dev/sdb5            1306        5714    35415261    b  W95 FAT32
root@ubuntu:~#

Also, what is listed doesn't seem to match up - it's as if the install worked on sdb and didn't do anything on sda.

What do you think?  Have I stuffed it up?

Thanks.

Ben

---

### Post by beninpoland on 2007-12-06
OK, bit more googling and I reckon this is my problem:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

My so called hardware RAID controller is fake! This is probably why I am having my booting problems and why Ubuntu sees the underlying disks, and why now they are out of synch....

Thanks for your time helping me. I am really learning a lot which I guess is a good thing.

Thanks again.

Ben

---

### Post by forestpixie on 2007-12-06
I know about absolutely nothing when it comes to raid :)

so I assume that will help you 
good luck

---

