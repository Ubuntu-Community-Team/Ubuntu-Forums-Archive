---
title: "Partition size/Disk performance/Cooperation"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by joechummer on 2008-06-08
I'm planning on rebuilding my PC with a WinXP/Ubuntu dual boot, and I've only been using Linux for less than 3 months.

My question is about partitioning.  I know you can install Ubuntu inside Windows without needing a dedicated Linux partition, but supposedly there is a noticeable hit in disk performance, which I'm assuming is due to Ubuntu running from NTFS instead of Linux's native ext3 file system.

To this end I plan on partitioning my drive to give Ubuntu its own native ext3 space and use the Windows partition for storing files that would be used for both OSes, since I'm assuming Windows will probably refuse to read an ext3 partition.

Which brings me to these points of contention:

1.  What size of partition should I give Ubuntu on an 80GB drive if I plan on keeping most of my non-Linux files on the Windows partition.  I know Ubuntu is about 2GB, but how much room should I leave on the partition for Linuz programs, swap, etc?  I'm worried if I make it too small, I'll run out of space too quickly, and if I make it too big, I'll run out of space on my Windows partition.

2.  Will storing most of my files on an NTFS partition cause a disk performance hit in Ubuntu anyway?  Or is it just Ubuntu running in NTFS space that causes disk performance issues?

3.  Can Windows read ext3?  If I boot into XP, will I even be able to access any files in my Ubuntu home directory, for example?

4.  Is Ubuntu's disk performance hit when installed on top of Windows that noticeable?  Would I be better off just installing Ubuntu on the same partition as Windows?

---

### Post by mikewhatever on 2008-06-08
> 1. What size of partition should I give Ubuntu on an 80GB drive if I plan on keeping most of my non-Linux files on the Windows partition. I know Ubuntu is about 2GB, but how much room should I leave on the partition for Linuz programs, swap, etc? I'm worried if I make it too small, I'll run out of space to quickly, and if I make it took big, I'll run out of space on my Windows partition.

It depends what programs you install and how many, by around 10 gb should be plenty. Swap is a separate partition. 1 GB should be OK for most users, just don't make it x2 your RAM if there is 2 GB of RAM installed.

> 2. Will storing most of my files on an NTFS partition cause a disk performance hit in Ubuntu anyway? Or is it just Ubuntu running in NTFS space that causes disk performance issues?

It should not. Personally, I don't like using system partitions for data storage, since one can easily delete an important system file or directory by accident.. A separate data partition can be used instead.

> 3. Can Windows read ext3? If I boot into XP, will I even be able to access any files in my Ubuntu home directory, for example?

Not natively. There is a driver to add ext2 support [http://www.fs-driver.org/](http://www.fs-driver.org/).

---

### Post by joechummer on 2008-06-09
Thanks for the advice!

Everything turned out okay, and my system dual boots with no problem.

My Ubuntu partition only took about an hour to install, update, and configure.  I'm **still** working on my Windows partition, even after 4+ hours, and there are still some drivers I can't even find.

Ubuntu - 1
Windows - 0

---

### Post by Habbit on 2008-06-09
> **joechummer said:**
> 2.  Will storing most of my files on an NTFS partition cause a disk performance hit in Ubuntu anyway?  Or is it just Ubuntu running in NTFS space that causes disk performance issues?
What might be noticeable is the CPU performance hit when writing to NTFS partitions, particularly if writing very large files (i.e. HD movies) to fragmented partitions. The ntfs-3g driver is very stable, but still not optimized enough CPU-wise.

> **joechummer said:**
> 3.  Can Windows read ext3?  If I boot into XP, will I even be able to access any files in my Ubuntu home directory, for example?
There are many tools to read and even write ext2/3 partitions, and even to read reiserfs partitions. There is one in particular, [ext2fsd]("http://ext2fsd.sourceforge.net/"), that allows you to have your ext2/3 partitions visible as normal Windows drives, as it is an IFS (installable filesystem driver) that gets loaded into the Windows kernel.

---

