---
title: "Multiboot and Swap partition question"
date: 2005-08-19
forum: Installation &amp; Upgrades
---

### Post by blastus on 2005-08-19
I have Windows XP and Mepis installed. I recently rebuilt my partition table from scratch so that I could install a third OS. Here is my layout:

```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9109    73168011    7  HPFS/NTFS
/dev/hda2            9110       13025    31455270   83  Linux
/dev/hda3           13026       13286     2096482+  82  Linux swap / Solaris

Disk /dev/hdb: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3738    30025453+   c  W95 FAT32 (LBA)
```

I want to install Ubuntu on /dev/hda4. Right now /dev/hda4 does not exist because I haven't created it yet but it will be a 10Gb partition. I have Mepis on /dev/hda2 and it uses /dev/hda3 as its swap partition. 

My question is, if I install Ubuntu on /dev/hda4 is it going to share/steal or otherwise the swap partition on /dev/hda3 from Mepis? If so would it affect my Mepis installation? Do swap partitions in Linux contain any permanent information in them? Are they shared between Linux distributions?

---

### Post by giopas on 2005-08-19
don't worry: swap partition will be shared from both unix sistems, and will be automatically detect from the ubuntu installation tool.

enjoy, ;)
giopas

---

### Post by blastus on 2005-08-19
Thanks giopas. I kind of suspected that might be the case that the Swap partition would be shared since you can't use two different Linux distributions at the same time.

---

