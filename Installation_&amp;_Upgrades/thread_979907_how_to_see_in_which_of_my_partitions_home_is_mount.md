---
title: "how to see in which of my partitions /home is mounted"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by vamsi Katneni on 2008-11-12
Hi,

How to see where my /home is mounted and how much is used and makr it to mount on other drive 

my /etc/fstab Contents are :- 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=4e4a92c8-8aa3-4f6c-a20e-d425c84c20fc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=22bf9930-ae6d-402e-b236-82140fad6d2c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


and fdisk -l gives the following:-Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd09bd09b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913       17512   125307000    f  W95 Ext'd (LBA)
/dev/sda3           17513       19457    15623212+  77  Unknown
/dev/sda5            1913        4236    18667498+  83  Linux
/dev/sda6            5738        9562    30724281    7  HPFS/NTFS
/dev/sda7            9563       13387    30724281    7  HPFS/NTFS
/dev/sda8           13388       17512    33134031    7  HPFS/NTFS
/dev/sda9            4433        5737    10482381   83  Linux
/dev/sda10           4237        4432     1574338+  82  Linux swap / Solaris

Partition table entries are not in disk order


and the boot flag is not set for Linux partition. I tried using gparted to set the Boot flag for /dev/sda9 on which root is mounted

---

### Post by taurus on 2008-11-12
```
df -h
```

Do you have a separate /home partition because it doesn't show in /etc/fstab?

---

### Post by caljohnsmith on 2008-11-12
> **vamsi Katneni said:**
> 
and the boot flag is not set for Linux partition. I tried using gparted to set the Boot flag for /dev/sda9 on which root is mounted
You don't need to set the boot flag on a partition for Grub to boot it; that is for brainless boot loaders like the Windows MBR (Master Boot Record) that just boots whichever partition on the HDD that has the boot flag set on. But even though Grub doesn't care about the boot flag, it is important that one of your partitions have the boot flag set, because some BIOSes will refuse to boot a drive if the boot flag is not marked on one of the partitions. :)

---

### Post by vamsi Katneni on 2008-11-12
Hi taurus,
 if we have seperate /home partition it won't show us the partition in the /etc/fstab file ?

---

### Post by y@w on 2008-11-12
> **vamsi Katneni said:**
> Hi taurus,
 if we have seperate /home partition it won't show us the partition in the /etc/fstab file ?

It will show in /etc/fstab if you created it during the install. It looks like you do not. The best way is to do a 'df -h' to see what's mounted where.

---

