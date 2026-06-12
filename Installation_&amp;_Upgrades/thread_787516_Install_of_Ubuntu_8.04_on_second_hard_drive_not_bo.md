---
title: "Install of Ubuntu 8.04 on second hard drive not booting"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by G_wiz on 2008-05-08
I have two hardrives installed, one has Win XP and Ubuntu 7.10 set up as a dual boot and both work fine.  The second hardrive had windows on it and I wanted to install Ubuntu 8.04 on it.  So i ran the install disc and told it to use the entire second harddrive for the install.  All installs normally. 
When I get into grub it does not show the new 8.04 distro, it shows the old Win XP in the grub menu instead.  
Do I need to reformat the hardrive or can I just move some files around to make it work?  I'm still pretty new to ubuntu and would appreciate any help!
Thanks.

---

### Post by NJC on 2008-05-09
I assume you are still booting from the 7.10 drive? If so, try swapping the boot order in your BIOS so the Ubuntu 8.04 drive starts first.

---

### Post by G_wiz on 2008-05-09
Yeah so I tried swapping the boot order in BIOS. Grub still showed Win XP and when I tried to boot 7.10(Gusty) it gave error 22, which i fixed by swapping boot order in BIOS the first time I installed Gusty...But thanks, I didn't think of trying that. 

Here is my fdisk:
G_wiz@G_wiz-Linux-desktop:~$ sudo fdisk -l
[sudo] password for G_wiz:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2bab359d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25942   208376248+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2           25942       29779    30822120    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           29780       38411    69336540   83  Linux
/dev/sda4           38412       38776     2931862+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05360535

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       13995   112414806   83  Linux
/dev/hdb2           13996       14593     4803435    5  Extended
/dev/hdb5           13996       14593     4803403+  82  Linux swap / Solaris
josh@josh-Linux-desktop:~$ /boot/grub

---

### Post by NJC on 2008-05-09
Hopefully some more seasoned users can chime in. But in the mean time, a few more things:

- I only see 2 bootable partitions, sda1 and sdb1. I'm assuming sda3 is the 7.10 partition, but it's not bootable.

- I wonder if the error msg "Partition 1 does not end on cylinder boundary." is causing trouble?

What I would expect with this configuration is that you would boot off of sdb1 (8.04), and it would include Grub entries for both XP and 7.10. There's probably a way to do this without a reinstall, but I don't know how.

---

