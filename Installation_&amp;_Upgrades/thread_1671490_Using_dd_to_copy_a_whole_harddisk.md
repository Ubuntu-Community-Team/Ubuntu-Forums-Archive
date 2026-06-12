---
title: "Using dd to copy a whole harddisk?"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by busfahrer on 2011-01-20
Hi,

I hope this is the right place for this question:

I'm going to replace the primary hdd of my box with another one of a different manufacturer, but of the same size (long story, never mind)

My current plan so I won't have to reinstall my system is booting from a Ubuntu CD (or USB stick, whatever) and doing
```

dd if=/dev/sda of=/dev/sdb

```

(If sdb happens to be a few megabytes smaller it doesn't matter, the last partition is not important)

Now my questions:

      1. Is this going to work? Is it a bad idea?
      2. Should I use any parameters for dd, for performance? Like setting bs (or something) to a bit smaller than the both HDD's (equal) cache size?
      3. Any other comments? All are appreciated.

If that matters, the hdd contains both NTFS, ext3/4 and reiserfs partitions. I use grub to boot Ubuntu, WinXP and Win7. 

Greetings,
busfahrer

---

### Post by wkulecz on 2011-01-20
I'd use something like Ghost for the Windows partitions and then do the Linux stuff with rsync and be prepared to re-install grub.

I do use rsync on NTFS partitions and it seems to work fine, but these are not Windows system partitions but external USB hard drives -- I back the files up to a 2TB drive formated ext4.

I'd worry that when you do the dd copy the partitions can get messed up because the c,hd,sec stuff that definces the boundries can be different for the same sized partiton on different drives.

OTOH, let us know how it goes if you try.  You can always do it the peicemeal way I suggested if dd leaves the systems on the new disk not working correctly.

---

### Post by psusi on 2011-01-20
Assuming that the new drive is exactly the same size, or larger, dd will work, but take ages since it will also copy the free space.  Ghost4Linux or clonezilla are better choices since they have a simple gui and are smart enough to skip the free space, and resize the fs to use any additional space on the new drive.  You can find both on the bootable parted magic cd.

---

### Post by srs5694 on 2011-01-20
> **wkulecz said:**
> I'd worry that when you do the dd copy the partitions can get messed up because the c,hd,sec stuff that definces the boundries can be different for the same sized partiton on different drives.

This isn't an issue on modern disks. Anything over roughly 8 GB (I don't recall the precise figure) maxes out the CHS values; only the LBA values are relevant, and they don't depend on the disk's CHS geometry. Thus, the suggested dd copy will work from a smaller to a larger disk if the original uses the MBR partitioning scheme (see below for my own caveat). If the final partition is unimportant, even a copy from a larger to a slightly smaller disk will work; you might just have to delete that final partition in fdisk after the fact (GParted will probably say the disk is unpartitioned if you use it on such a disk).

Psusi's comments are valid; however, using the more sophisticated tools he suggests may involve more investment in *human* time, even if it speeds up the copying. If you're happy to set the copy going, go to bed, and deal with the result the next day, the dd copy may involve less time investment by you. So take your pick which is more important: Your time at the keyboard or quicker copying results.

Now, my caveat: If by chance the disk uses the GUID Partition Table (GPT) system rather than MBR, then the dd copy will either put the backup GPT data in the wrong place or omit it entirely if the disks differ by as much as one sector in size. This problem is easily correctable, but it may cause confusion and some partitioning tools may flake out on such disks. (Apparently some versions of GParted do so, but others correct the problem automatically.) Most disks used in PCs today use MBR rather than GPT, so chances are this won't be a problem, but I thought I'd mention it just for the sake of completeness.

---

### Post by C.S.Cameron on 2011-01-20
> **busfahrer said:**
> Hi,

I hope this is the right place for this question:

I'm going to replace the primary hdd of my box with another one of a different manufacturer, but of the same size (long story, never mind)

My current plan so I won't have to reinstall my system is booting from a Ubuntu CD (or USB stick, whatever) and doing
```

dd if=/dev/sda of=/dev/sdb

```

(If sdb happens to be a few megabytes smaller it doesn't matter, the last partition is not important)

Now my questions:

      1. Is this going to work? Is it a bad idea?
      2. Should I use any parameters for dd, for performance? Like setting bs (or something) to a bit smaller than the both HDD's (equal) cache size?
      3. Any other comments? All are appreciated.

If that matters, the hdd contains both NTFS, ext3/4 and reiserfs partitions. I use grub to boot Ubuntu, WinXP and Win7. 

Greetings,
busfahrer


I use the method you show and it works fine for me, new drive ends up bootable and everything.
Only dif is sdb is larger than sda.

---

### Post by presence1960 on 2011-01-20
[Clonezilla]("http://clonezilla.org/")

---

