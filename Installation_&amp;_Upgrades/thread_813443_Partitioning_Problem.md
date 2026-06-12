---
title: "Partitioning Problem"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by cyberyoda0 on 2008-05-30
So I was attempting to install Ubuntu 8.04 as a dual boot with WinXP on my cousins computer.  I tried running the OS from the CD, but it froze, so I manually turned the computer off. When I booted up from the CD again, I chose to install rather than Try Ubuntu.  When I got to the partition manager, there was an extra partition.  I have ~40 Gig hard-drive, and it had two 18.5 partitions, with one of them almost completely full.  I assumed this was where windows was, but I knew Windows would need more room.  So I used the manual partition manager and created a new partition table so I could make the full partition (with windows) larger, and to create a new 10Gb partition for Ubuntu & Swap.

As for the 30Gb partition, I selected the option "do nothing to this partition" (or something along those lines) so it would keep Windows on the 30Gb partition.

But now it looks like I overwrote the Windows partition with the "do nothing" option because WinXP isn't showing up on the boot menu.  This is my fdisk -l and it looks like there's no NTFS on there.

```
Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3647    29294496   83  Linux
/dev/sda2   *        3648        4802     9277537+  83  Linux
/dev/sda3            4803        4863      489982+  82  Linux swap / Solaris
```

Did I just delete windows completely?  Is it recoverable?

(Sorry I'm stupid, and thanks for your help!)

---

### Post by abhiroopb on 2008-05-30
Haven't done an install in a while so I can't remember what each option does, but at least according to this I can't see any chance of windows being there. Try this to check though, see if you can mount the 30gb "linux" file system (/dev/sda1) and see whats there. Also double-check in gparted. But yea looks like the Windows is gone.

---

### Post by cyberyoda0 on 2008-05-31
Going to Places >> Computer  I'm not able to see the 30Gb hard drive.  Is there another way to mount the drive?

I've never used gparted before.  Here's what it shows.

---

### Post by galileon on 2008-05-31
> **cyberyoda0 said:**
> So I used the manual partition manager and created a new partition table so I could make the full partition (with windows) larger, and to create a new 10Gb partition for Ubuntu & Swap.


"New partition table"? Sounds bad to me. Did you actually destroy the partitions on there and created new ones all over the disk? if so, yes, its probably irrecoverable by now (though you may be able to extract some lost files at great pain).

The idea of manual, when you want to keep some partitions, is to avoid touching them at all, but simply use space that's free or that belongs to partitipns you want to delete.

Sorry.

---

### Post by abhiroopb on 2008-05-31
type this into the terminal:

```

sudo mkdir /media/fat
sudo mount /dev/sda1 /media/fat

```

This shuld mount that fat16 hard drive. Mount it and see if you can acess it.

---

