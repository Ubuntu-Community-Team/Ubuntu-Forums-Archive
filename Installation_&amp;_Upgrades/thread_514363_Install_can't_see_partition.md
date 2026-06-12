---
title: "Install can't see partition"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by bladez on 2007-07-31
Ok, here is the deal.

I wan't to dual boot Ubuntu + WinXP. I have already installed XP and my partitions are:

1. C: [NTFS, 70gb, my WinXP boot&system partition (free 20gb)]
2. D: [NTFS, 60gb, my file storage(free 6gb)]
3. Unallocated Space [9 GB(an formated ex-MACOSX partition]

The thing is, when i try to install Ubuntu, he gives me 2 options. 

Guided - use all HDD (delete all data) or
Manual

so ofcourse i pick manual. But in manual, all he shows is just the HDD, giving me no choice, but to format it and use all HDD space. He shows no partitions. He also shows the same in GParted.

What to do? I wan't to keep my XP.

Besides, i can't run Partition Magic, bcause he shows this error:

```
Error 117: Partition's drive letter cannot be identified
```

HELP!

---

### Post by Pumalite on 2007-07-31
Use Gparted to shrink your XP partition: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Then you can use 'Guided-Largest Available Space' or 'Manual', which I recommend. It allows you to create extended partitions that you can determine size and where to mount. 10 GB for '/' is minimum; 500 MB to 1 GB for Swap, the rest for '/home/

---

### Post by bladez on 2007-08-01
mmmm.....isn't GParted already included in Ubuntu. I'm trying to install Ubuntu 7.04 Feisty!

Anywayz, GParted doesn't show any partitions on my HDD. Also it gives me only the option to delete the whole HDD, in order to make some kind of file (a file, that records every partition). I can't afford to lose my whole data on my HDD.

Bsides, here is a log report from PartitionInfo:

```

Error #105: Partition didn't begin on head boundary.
  ucBeginHead expected to be 0 or 1, not 136.
Error #105: Partition didn't begin on head boundary.
  ucBeginHead expected to be 0 or 1, not 16.
Error #108: Partition didn't end on cylinder boundary.
  ucEndHead expected to be 254, not 239.

```

I can't correct these errors with CHKDSK in no way. Hmmm....it looks like somethings wrong with the MFT.

---

### Post by Pumalite on 2007-08-01
Gparted allows you to 'shrink' the partition you have and therefore creating a new partition.

---

### Post by fredj on 2007-08-01
Is your disk drive a standard IDE drive of is it a SATA drive?

---

