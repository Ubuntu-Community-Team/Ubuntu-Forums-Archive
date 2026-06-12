---
title: "[SOLVED] gparted - unallocated hard drive!!!"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by varun.net on 2008-09-29
I installed Ubuntu 8.04 from a cd, clean install on the whole hard disk. Used ubuntu's partition manager, and did custom partitioning with the following config

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c7e3c7d

Device Boot Start End Blocks Id System
/dev/sda1 * 1 622 4996183+ 83 Linux
/dev/sda2 623 19208 149292045 83 Linux
/dev/sda3 19209 19457 2000092+ 82 Linux swap / Solaris

/dev/sda1 - /
/dev/sda2 - /home
/dev/sda3 - /swap


Didn't change anything since then. Now the root partition [/dev/sda1] is running out of space. I need to resize it.

But when I load up gparted live cd it sees unallocated space on /dev/sda.
I have tried knoppix live cd same thing.

I also tried testdisk but it said everything was fine/healthy no problems.



Does anybody know what might be wrong and how can it can fixed so that

    * i can reduce /dev/sda2 and increase /dev/sda1

    * maybe if at all possible install windows in the remaining empty space derived from /dev/sda2

---

### Post by cariboo on 2008-09-30
Are you sure you are trying to resize the partition with the disk unmounted?

Jim

---

### Post by varun.net on 2008-10-01
> **cariboo907 said:**
> Are you sure you are trying to resize the partition with the disk unmounted?

Jim

I believe they are unmounted, since I am booting from a gparted live cd/knoppix live cd. Correct me if I am wrong, what I am guessing is that any live cd won't be mounting the hard disks automatically unless it is specified via a command through the terminal.

I will check again and confirm.

---

### Post by varun.net on 2008-10-10
> **varun.net said:**
> I believe they are unmounted, since I am booting from a gparted live cd/knoppix live cd. Correct me if I am wrong, what I am guessing is that any live cd won't be mounting the hard disks automatically unless it is specified via a command through the terminal.

I will check again and confirm.


Confirmed, the disks are not mounted when I run gparted from a live cd.

Ran testdisk, which rewrote the partition table and still gparted cannot see anything while at the same time fdisk works absolutely fine.

Also tried qparted which comes with knoppix live cd and even it cannot read the partition table and show me and empty/unallocated hard disk.

Please HELP!!!

---

### Post by varun.net on 2008-10-13
Finally I solved it. Thanks but no thanks Ubuntu forums.


[LIST]
Boot from a live cd which has test disk utility (gparted live cd). 
[/LIST]

[LIST]
Open up a terminal once you have booted from the live cd and run testdisk and write the partition table to disk [analyze>proceed>write].
[/LIST]

[LIST]
Now run gparted and it will recognize all the partitions
[/LIST]


Note:- Running testdisk from inside of the ubuntu installation won't help.

---

### Post by varun.net on 2008-10-13
> **varun.net said:**
> Finally I solved it. Thanks but no thanks Ubuntu forums.


[LIST]
Boot from a live cd which has test disk utility (gparted live cd). 
[/LIST]

[LIST]
Open up a terminal once you have booted from the live cd and run testdisk write the partition table to disk.
[/LIST]

[LIST]
Now run gparted and it will recognize all the partitions
[/LIST]


Note:- Running testdisk from inside of the ubuntu installation won't help.



Thank you Varun!!!

---

