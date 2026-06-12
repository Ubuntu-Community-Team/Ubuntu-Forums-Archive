---
title: "Partition problems"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by xagentcooper on 2011-05-28
Hello.

I am trying to install Ubuntu 11 to dual-boot with Windows 7 (my main os).
  Here is screenshot of disk management on Windows [http://i.stack.imgur.com/4ZurV.jpg](http://i.stack.imgur.com/4ZurV.jpg)


As you can see I already shrinked volume D: for 16gb, where I am  about to install ubuntu. However, in Ubuntu installation, I see no  partitions at all.
  Then, I launched Disk utility, and here what it showed: [http://i.stack.imgur.com/tvZ8i.png](http://i.stack.imgur.com/tvZ8i.png)


Check the size of last out-of-nowhere partition. Obviously something is wrong with my partition table. What can I do? Thanks.


Also, gparted screenshot [http://i.imgur.com/yZOi8.png](http://i.imgur.com/yZOi8.png)

---

### Post by srs5694 on 2011-05-28
You've probably got a damaged partition table, as described [here.](http://www.rodsbooks.com/missing-parts/index.html) If so, the easiest solution is to use my [FixParts](http://www.rodsbooks.com/fixparts/) program. If you need a more precise diagnosis, please boot the Ubuntu installer into "live CD" mode and run the following command:

```

sudo fdisk -lu

```

Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility.

---

### Post by xagentcooper on 2011-05-28
Here is the fdisk result:

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4f494d44

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    31459327    15728640   27  Unknown
/dev/sda2   *    31459328    31664127      102400    7  HPFS/NTFS
/dev/sda3        31664128   504213503   236274688    7  HPFS/NTFS
/dev/sda4       504213507   976784129   236285311+   f  W95 Ext'd (LBA)
/dev/sda5       504215552   943214591   219499520    7  HPFS/NTFS


```I should run fixparts under ubuntu?

---

### Post by srs5694 on 2011-05-28
Yes, FixParts should handle that easily. The problem is a common one: Your extended partition (/dev/sda4) is larger than the disk -- check the end sector value vs. the total number of sectors on the disk. Fortunately, the one partition it contains is within legal limits, so the problem is easily corrected by creating a fresh extended partition (which is what FixParts does, among other things).

---

