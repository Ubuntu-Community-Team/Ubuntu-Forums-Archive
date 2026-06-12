---
title: "Help Reinstalling GRUB"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by mysticalone on 2008-03-26
I had Ubuntu and XP dual boot on my SATA, I unplugged it installed Vista on an IDE disk. I placed them all together tried to get vista to work in grub but didn't work so I figured forget it, I'll just reinstall Vista with both disks and reinstall grub. Well, it didn't go well and Vista fudged my MBR and I'm currently on a Live CD.

My map right now is
hd0 -> /dev/hdd <- Vista drive
hd1 -> /dev/sda <- Previous Ubuntu and XP dual boot drive

hdd is set to slave. everytime I type find /boot/grub/stage1 I get a file not found.
everytime I try selecting another disk, I get a disk not found.

pls, i've got to fix this.

---

### Post by Pumalite on 2008-03-26
To reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
(I'm nor sure it will work for you)

---

### Post by mysticalone on 2008-03-26
Thats the same page everyone keeps sending me to and it doesn't help.

---

### Post by Pumalite on 2008-03-26
That's what I thought. Let's start from scratch because you problem is different. Post:
sudo fdisk -lu

---

### Post by mysticalone on 2008-03-26
> Disk /dev/hdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe71dc794

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *        2048    78796799    39397376    7  HPFS/NTFS
/dev/hdd2        78796800   195530751    58366976    7  HPFS/NTFS

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x78477847

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    83891429    41945683+   7  HPFS/NTFS
/dev/sda2        83891430   263787299    89947935    f  W95 Ext'd (LBA)
/dev/sda3       263787300   347566274    41889487+  83  Linux
/dev/sda4       347566275   354650939     3542332+  82  Linux swap / Solaris
/dev/sda5        83891493   104856254    10482381    7  HPFS/NTFS
/dev/sda6       104856318   115346699     5245191    7  HPFS/NTFS
/dev/sda7       115346763   136311524    10482381    7  HPFS/NTFS
/dev/sda8       136311588   146801969     5245191    7  HPFS/NTFS
/dev/sda9       146802033   157292414     5245191    7  HPFS/NTFS
/dev/sda10      157292478   263787299    53247411    7  HPFS/NTFS

That's what I get

---

### Post by Pumalite on 2008-03-26
Read this:
[http://ubuntuforums.org/showthread.php?t=46003](http://ubuntuforums.org/showthread.php?t=46003)

[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

