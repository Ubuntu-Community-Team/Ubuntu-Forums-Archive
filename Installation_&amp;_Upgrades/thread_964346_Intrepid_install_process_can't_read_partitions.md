---
title: "Intrepid install process can't read partitions"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by djrobthaman on 2008-10-30
Hi,

I'm trying to install intrepid but I can't because even though gparted reads all my partitions, when I run the install process and get to the partition section I only see an empty window (screenshot attached).

Has anyone encountered this?  Any suggestions on how to force it to see my partitions?

Thanks

---

### Post by VMC on 2008-10-30
Yes, somethings wrong with the partitioning program. When I run gparted from LiveCD it shows hard drive but no partitions.

When I try to install either from startup or from after bootup from LiveCd. I get to the partitioning sequence and tell it I want manual. It then shows the entire drive as /dev/sda. It shows NO partitions. I have about 7 partitions.

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb5ffb5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10490413+   7  HPFS/NTFS
/dev/sda2            1307       20023   150344302+   5  Extended
/dev/sda4            4494        4822     2642692+  82  Linux swap / Solaris
/dev/sda5            1307        2713    11301696   83  Linux
/dev/sda6            2714        4493    14297818+  83  Linux
/dev/sda7            4823       16676    95217223+   7  HPFS/NTFS
/dev/sda8           16677       17951    10241406   83  Linux
/dev/sda9           17952       20023    16643308+  83  Linux

---

### Post by djrobthaman on 2008-10-30
Okay, so I'm now running intrepid.  Here's what I did.



....
...
..
.


I went through the install process BEFORE opening the partition editor.  I don't know why, but clearly the fact that I opened it before I got to that stage in the install process just messed up the whole process.

Don't know if that'll be any help to you or anybody else, but I give it to you how it happened.

---

### Post by VMC on 2008-10-31
I'm now also running Ibex. My issue was different. It turned out to be an error with an extended partition. It didn't show its face until I deleted another partitions. Also, two NTFS partitions, one including Windows, had errors. It was a mess, but I have it all squared away.

---

### Post by rameshg87 on 2008-11-02
I think the problem happens because of one or more mounted filesystems on the livecd that has just booted. What I did was I unmounted all the filesystems. Just try if that works for you. For me sda1 was mounted. Run "mount" to see where the partitions are mounted and just unmount those partitions.

$ mount 

$ sudo umount -l /mount-point

$ sudo partprobe /dev/sda

---

### Post by naaman on 2008-11-02
Both the normal and the alternate installation CDs are displaying that they can only see one large 320GB hard disk and are only offering to wipe the whole thing before proceeding further with the install.

I have no disks mounted at the time I am running these installs and I have tried out the unmounting procedures as well..

Hardy detected the Vista partition that is pre-installed by Dell on my machine, what's up with Intrepid??

```
naaman@perkynana:~$ sudo fdisk -l
[sudo] password for naaman: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       38587       38914     2620416    c  W95 FAT32 (LBA)
/dev/sda2              11        1316    10485760    7  HPFS/NTFS
/dev/sda3   *        1316        5754    35648437+   7  HPFS/NTFS
/dev/sda4            5755       38914   266350820+   f  W95 Ext'd (LBA)
/dev/sda5           38587       38914     2620416   dd  Unknown
/dev/sda6            5755       37263   253096011   83  Linux
/dev/sda7           37264       38586    10626966   82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by rameshg87 on 2008-11-02
Did you do this before starting ubuntu install ??

sudo partprobe /dev/sda

---

### Post by naaman on 2008-11-03
> **rameshg87 said:**
> Did you do this before starting ubuntu install ??

sudo partprobe /dev/sda
Sure did, I got a message back about overlapping partitions..

I have just ended up performing a dist-upgrade via the graphical upgrade manager in Hardy instead.
Had to upgrade my BIOS (Dell XPS M1330) to turn off the noisy fan on the NVidia GPU otherwise, Intrepid looks alright.

---

