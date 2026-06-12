---
title: "Full Ubuntu 10.10 install"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by Kramer2010 on 2011-01-04
I am currently dual booting Ubuntu 10.10 and Win 7 (very successfully) and I was wondering if it was possible to remove windows completely without a fresh installation from scratch (ie wipe the windows partition and absorb it into Ubuntu).  Not planning to do this, but the idea intrigued me.

---

### Post by coffeecat on 2011-01-04
So long as you have Ubuntu on its own partition(s) and not a Wubi install this is possible. You would delete the Windows partition(s) and then use a live CD to resize your Ubuntu partition to fill the released space. Or perhaps to create more partitions that could be used for data storage.

There might be some complications. If  you had Ubuntu on  primary partitions, they might get renumbered as soon as you deleted the Windows ones. In which case you would have to do some deft work on grub using the live CD. But if your Ubuntu partitions were logical ones, this would probably not be necessary.

If you were contemplating doing this, post the output of:

```
sudo fdisk -lu
```... and someone would be able to advise.

---

### Post by West201 on 2011-01-04
Delete Windows Partition with Disk Utility from System<Admin

Download gparted & burn it to CD 


gparted.sourceforge.net/download.php

Then add the free space to Ubuntu

---

### Post by Dex73 on 2011-01-04
g-parted is on the install cd. Just choose the try it out option and go to System. I think it's under Administration. There's no need to download and burn it separately.

---

### Post by Kramer2010 on 2011-01-05
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x43764375

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    26626047    13312000   27  Unknown
/dev/sda2   *    26626048    26830847      102400    7  HPFS/NTFS
/dev/sda3        26830848   352447151   162808152    7  HPFS/NTFS
/dev/sda4       352450558   625141759   136345601    f  W95 Ext'd (LBA)
/dev/sda5       352450560   358742535     3145988    7  HPFS/NTFS
/dev/sda6       358744064   614236159   127746048   83  Linux
/dev/sda7       614238208   625141759     5451776   82  Linux swap / Solaris

---

### Post by coffeecat on 2011-01-05
It's more complicated than anticipated but doable. You have:

sda1 = 13.6GB - probably a manufacturer's restore partition.
sda2 = 104MB - probably your Windows 7 boot partition.
sda3 = 166.7GB - presumably your Windows C: partition.

Then sda4, which is an extended partition which contains the logical partitions:

sda5 - 3.2GB - a NTFS partition. What is this? It's a bit small for a Windows D: or E: partition.
sda6 = 130.8GB - your Ubuntu root partition.
sda7 = 5.6 GB - your swap partition.

If sda1 is a restore partition, you would probably want to keep it. Partitions sda2 and sda3 could (theoretically) be deleted, which would leave nearly 167GB free space to the left of the extended partition. You would need to resize the extended partition back into the free space before you could enlarge sda6. However, that peculiar sda5 NTFS partition is in the way and you wouldn't be able to enlarge sda6 without removing sda5.

Alternatively if you remove the Windows partitions, instead of enlarging your Ubuntu root partition, which is huge, you could create a partition or partitions for data storage - perhaps a separate /home. This could be a primary partition or, if you enlarge the extended partition, a logical partition(s).

You have many possible options. You may want to read this link and all it links to:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Having said all that I note you said in your first post that this was just an idea, not an immediate plan.

---

