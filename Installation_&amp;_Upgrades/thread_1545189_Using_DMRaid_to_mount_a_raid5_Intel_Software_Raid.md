---
title: "Using DMRaid to mount a raid5 Intel Software Raid"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by Lush on 2010-08-03
Hey Guys,

I'm trying to connect to my intel software raid that I made in windows. It's just a 4.2 TB Array -- no partitions on it... just the file system.

I'm running on a Asus p6t deluxe v2 which has a x58 northbridge and a ich10r southbridge. My friend said something about my linux kernel not having the proper drivers for use with my northbridge, but a cursory google search could not find anything. What I could find is other people having similar difficulties with my motherboard. If it helps I'm running Linux 2.6.32-24-generic.

Before anyone suggests I do a pure linux software raid a la mdadm, know that under my current situation, I need to run Windows as well and access the data on my raid from both partitions. 

Now Since it's gpt on the raid, fdisk gets angry about displaying it, but in anycase here is the output.

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8aa8e3b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       70528   566406250    7  HPFS/NTFS
/dev/sda3           70529       77825    58613152+  83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
256 heads, 63 sectors/track, 181688 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      266306  2147483647+  ee  GPT

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f4eef6e

   Device Boot      Start         End      Blocks   Id  System

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f4eef6e

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
256 heads, 63 sectors/track, 181688 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      266306  2147483647+  ee  GPT

```

I assume it's bad that it's not grouping it together?

So next I try fdisking the raid (i don't know what to call it) but its in /dev/mapper... and I get this

```
root@blackdragon:/home/khanh# fdisk -l /dev/mapper/isw_bhdagjbegb_Orange 

WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/isw_bhdagjbegb_Orange'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/mapper/isw_bhdagjbegb_Orange: 4500.9 GB, 4500898578432 bytes
256 heads, 63 sectors/track, 545065 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

                            Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_bhdagjbegb_Orange1               1      266306  2147483647+  ee  GPT

```

I find it odd that it's not finding /dev/mapper/isw_blahblah_Orange2

So, I open it up in gparted via 

```
gparted /dev/mapper/isw_blahblah_Orange
```

I see both Orange1 & Orange2 (Orange1 being Windows made partition data and Orange2 being the actual data I care about)

There is a warning along the lines of :

```

The device on /dev/mapper_isw_blahblah_Orange2 doesn't exist.

ntfsresize v2.0.0 (libntfs 10:0:0) ERROR(2) Failed to check /dev/mapper/isw_blahblah_Orange2  mount state no such file or directory. Probably /etc/mtab is missing. It's too risky to continue. Try another Linux distro.




```

Anyone have any ideas?

---

### Post by ronparent on 2010-08-03
Ideas depend on where you are trying to go. ie. Where and what OS's will be installed. How you create or manage the non linux partitions will depend on if you will be running win7. etc.

You don't say that you plan on installing 10.04 to your raid. In general, although the Ubuntu 10.04 desktop distribution includes a program called dmraid which is used to manage the raid partitions, it has omitted an ancillary program called kpartx which gparted needs installed also to properly see the raid partitions during the install. I have got around this to install on a raid 0 (same principle) by starting a 10.04 live cd session, 1st installing kpartx with sysnaptics, and then running an install from the same session. 

But i'm getting ahead of myself. If orange2 doesn't exist, there is probably a file system error you have to fix with win7 before you proceed. Once fixed, you should be able validly recognize it with gparted. You shouldn't try any operation on that partition with gparted - win7 is fussy.

Do post again if you still need help.

---

### Post by Lush on 2010-08-03
Thanks for your quick reply,

kpartx did the trick!! I Installed it and I was immediatly able to mount the array, Orange2 showed up in /dev/mapper too :). 

Major Props to you sir!

---

### Post by Lush on 2010-08-03
Something odd I just noticed,

Orange2, my device that has the raid5 array does not appear in /dev/mapper until I open gparted? this seems odd behavior to me...

---

