---
title: "Multiple installation partition disaster!"
date: 2018-11-12
forum: Installation &amp; Upgrades
---

### Post by alex-bingham on 2018-11-12
[SIZE=2][FONT=arial]Guys

On trying to upgrade to the 18.04, I made a couple of mistakes on the installations and when I went back to try and re-install, it kept generating new partitions (almost certainly my fault). I have a dual boot windows and linux but just want the one windows and one linux installation.  On analysing the partitions I get the following:
```
alex@Alex-PC:~$ sudo fdisk -l
Disk /dev/loop0: 144.4 MiB, 151375872 bytes, 295656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop1: 87.9 MiB, 92114944 bytes, 179912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/loop2: 87.9 MiB, 92123136 bytes, 179928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x1ff1bb3d

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            2048  31746047  31744000  15.1G 27 Hidden NTFS WinRE
/dev/sda2  *     31746048  31950847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda3        31950848 398747722 366796875 174.9G  7 HPFS/NTFS/exFAT
/dev/sda4       398749694 976771071 578021378 275.6G  5 Extended
/dev/sda5       586063872 852079496 266015625 126.9G 83 Linux
/dev/sda6       968693760 976771071   8077312   3.9G 82 Linux swap / Solaris
/dev/sda7       398749696 586063871 187314176  89.3G 83 Linux
/dev/sda8       963454976 968687615   5232640   2.5G 83 Linux
/dev/sda9       852080640 963450879 111370240  53.1G 83 Linux

Partition 4 does not start on physical sector boundary.
Partition table entries are not in disk order.

Disk /dev/sdb: 18.7 GiB, 20014718976 bytes, 39091248 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x1ff1bb13

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1        2048 39088127 39086080 18.7G 84 OS/2 hidden or Intel hibernation

```

This looks massively inefficient even to a non-techie guy like me.  Can anyone advise as to how I shrink/delete the redundant partitions to get more space?

Many thanks

A[/FONT][/SIZE]

---

### Post by TheFu on 2018-11-12
Use gparted or fdisk or parted.
Don't delete any partitions you might want to keep.

---

### Post by alex-bingham on 2018-11-12
Thanks.  As a newbie, can you give me a bit of guidance on how to use these tools.

---

### Post by TheFu on 2018-11-12
open the tool.
select the partition
choose "delete"
When you are done, tell the tool to "write the changes" or "apply"

Don't delete anything you might want or need.

---

### Post by alex-bingham on 2018-11-12
Thanks.  And will that resize the partitions?

---

### Post by slickymaster on 2018-11-12
*Thread moved to **Installation & Upgrades**.*

---

### Post by TheFu on 2018-11-12
> **alex-bingham said:**
> Thanks.  And will that resize the partitions?

Only if you tell it to do so.  Resizing can change the UUID which will break the install. Be prepared to fix the issue in the /etc/fstab by booting from the installation media, mounting the HDD partition, and editing the file correctly.  A good understanding of partitions, naming, UUIDs would be helpful.  Might need to reinstall grub and update it too.  

This all assumes you didn't choose to encrypt anything and didn't use LVM.

Your knowledge will expand greatly. If you aren't certain about all this, perhaps the easiest answer for a noob is to delete all the Linux partitions and do a fresh install using all that knowledge you've gained.  Perhaps.

---

