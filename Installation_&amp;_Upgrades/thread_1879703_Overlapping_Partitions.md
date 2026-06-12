---
title: "Overlapping Partitions"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by dimbohall on 2011-11-12
Hi,

I stupidly inserted the windows CD into my dual boot Ubuntu 11.10 / windows xp system. I just wanted to see if I could install windows on my external usb HD, but didn't actually go ahead with the install.

It seems like the windows CD messed up my MBR and I had to use boot-repair and the ubuntu 11.10 live CD to gain access to ubuntu again.

It seems to boot up a little differently (slower) but works. However, I now cant see any of my partitions in nautilus (there are 3) although I can mount them manually.

When I open gparted, it just shows my whole hard drive as unallocated (I know it has a windows partition that works and my ubuntu partition that I am using now). It gives an error 'cannot have overlapping partitions'.

Nothing will automount anymore, not even USB drives.

sudo fdisk -lu /dev/sda

gives

```
omitting empty partition (5)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x877b877b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    63842309    31921123+   7  HPFS/NTFS/exFAT
/dev/sda2        63844350   133484084    34819867+   5  Extended
/dev/sda3       127636488   133484084     2923798+  82  Linux swap / Solaris
/dev/sda4       133484085   625137344   245826630   83  Linux
/dev/sda5        63844352   123445247    29800448   83  Linux
/dev/sda6       123447296   127635455     2094080   82  Linux swap / Solaris
```

which shows they are overlapping.

How can I fix this?

Thanks,

D.

---

### Post by coffeecat on 2011-11-12
The overlapping partitions error message (and Gparted showing all unallocated space) is because the Windows XP installer has got up to its old trick of trying to convert a Linux logical partition into a primary one - which is impossible. If you look at your fdisk output you'll see that the swap partition (sda3) is inside your extended partition, sda2. Which is where it is meant to be if it is a logical one. It was a logical partition, and was probably originally numbered sda7, but the Windows installer thought it knew better and renumbered it to #3, which is primary by definition. You now have an illegality in the partition table, and various utilities are complaining as a result.

Easily fixed. Have a look here:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Fixparts *should* detect and fix the problem without much input from you, but what it needs to do is to rewrite the partition table so that sda3 becomes a logical partition once again.

By the way, the output of fdisk is near unreadable at the moment. It needs to be in code tags and I'll do that for you.

**EDIT**: I don't know what the "omitting empty partition (5)" message is all about. Perhaps more confusion caused by the partition table illegality.

---

### Post by dimbohall on 2011-11-13
> **coffeecat said:**
> The overlapping partitions error message (and Gparted showing all unallocated space) is because the Windows XP installer has got up to its old trick of trying to convert a Linux logical partition into a primary one - which is impossible. If you look at your fdisk output you'll see that the swap partition (sda3) is inside your extended partition, sda2. Which is where it is meant to be if it is a logical one. It was a logical partition, and was probably originally numbered sda7, but the Windows installer thought it knew better and renumbered it to #3, which is primary by definition. You now have an illegality in the partition table, and various utilities are complaining as a result.

Easily fixed. Have a look here:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Fixparts *should* detect and fix the problem without much input from you, but what it needs to do is to rewrite the partition table so that sda3 becomes a logical partition once again.

By the way, the output of fdisk is near unreadable at the moment. It needs to be in code tags and I'll do that for you.

**EDIT**: I don't know what the "omitting empty partition (5)" message is all about. Perhaps more confusion caused by the partition table illegality.

Hi,

Thanks. That worked perfectly. It did knock out grub which was easily repaired using the live disk and boot-repair.

Chao.

D.

---

### Post by coffeecat on 2011-11-13
> **dimbohall said:**
> It did knock out grub which was easily repaired using the live disk and boot-repair.

Curious. I wouldn't have thought it would touch the parts of the HD where grub is written. Whatever, I'm gad you got it fixed.

---

