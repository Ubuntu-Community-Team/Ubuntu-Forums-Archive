---
title: "Can't configure fake raid for dualboot PC"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by beninpoland on 2007-12-09
Hi

I am trying to follow the Fake RAID Howto tutorial here:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

to install Ubuntu 7.10 on a Dell Precision 380 which has fake raid and windows xp on already.

I am having problems configuring my RAID array and wondered if anyone
can help.  I set up my partitions using fdisk and parted as follows:

root@ubuntu:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ade8ade

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1305    10482381    7  HPFS/NTFS
/dev/sda2            1306        5714    35415292+   f  W95 Ext'd (LBA)
/dev/sda3            5715        9450    30009420   83  Linux
/dev/sda4            9451        9726     2216970   82  Linux swap /
Solaris
/dev/sda5            1306        5714    35415261    b  W95 FAT32

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ade8ade

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1305    10482381    7  HPFS/NTFS
/dev/sdb2            1306        5714    35415292+   f  W95 Ext'd (LBA)
/dev/sdb3            5715        9450    30009420   83  Linux
/dev/sdb4            9451        9726     2216970   82  Linux swap /
Solaris
/dev/sdb5            1306        5714    35415261    b  W95 FAT32

Partition 1 is for windows, 5 for shared data, 3 will be my linux root
and 4 for swap.

But when I ran dmraid -ay I got the following error:

root@ubuntu:~# dmraid -ay
RAID set "isw_dgdcajach_Volume0" already active
ERROR: dos: partition address past end of RAID device
RAID set "isw_dgdcajach_Volume01" already active
RAID set "isw_dgdcajach_Volume03" already active
RAID set "isw_dgdcajach_Volume05" already active

Also when I do dmraid -r it says "GROUP" and not "MIRROR", is that OK or
do I need to do something else? How do I tell dmraid/ubuntu that this
will be a raid-1 array?

root@ubuntu:~# dmraid -r
/dev/sda: isw, "isw_dgdcajach", GROUP, ok, 156249998 sectors, data@ 0
/dev/sdb: isw, "isw_dgdcajach", GROUP, ok, 156301486 sectors, data@ 0

Following the HowTo I expected to be able to run:

root@ubuntu:~# fdisk /dev/mapper/isw_dgdcajach

but that gives me:
Unable to open /dev/mapper/isw_dgdcajach

I have to run it as /dev/mapper/isw_dgdcajach_Volume0.  When I do command "p" I
see:

Disk /dev/mapper/isw_dgdcajach_Volume0: 79.9 GB, 79996911616 bytes
255 heads, 63 sectors/track, 9725 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ade8ade

                             Device Boot      Start         End
Blocks   Id  System
/dev/mapper/isw_dgdcajach_Volume0p1   *           1        1305
10482381    7  HPFS/NTFS
/dev/mapper/isw_dgdcajach_Volume0p2            1306        5714
35415292+   f  W95 Ext'd (LBA)
/dev/mapper/isw_dgdcajach_Volume0p3            5715        9450
30009420   83  Linux
/dev/mapper/isw_dgdcajach_Volume0p4            9451        9726
2216970   82  Linux swap / Solaris
/dev/mapper/isw_dgdcajach_Volume0p5            1306        5714
35415261    b  W95 FAT32

I tried to run mkfs -t on partition 3 but I get:

root@ubuntu:~# mkfs -t ext3 /dev/mapper/isw_dgdcajach_Volume0p3
mke2fs 1.40.2 (12-Jul-2007)
Could not stat /dev/mapper/isw_dgdcajach_Volume0p3 --- No such file or
directory

So I am now stuck and running out of ideas on how I can install Ubuntu
on this PC (I can't trash Windows XP yet as I need it for work at the
moment).

Any help or ideas much appreciated.

Thanks.

Ben

---

