---
title: "Format"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by caravanman on 2010-01-20
Is it best to format hard drive using NTFS or FAT32
For use with Ubuntu

---

### Post by underquark on 2010-01-20
What size hard drive and what do you plan on doing with it?  Normally ext3, sometimes ext2 or ext4 are used for ubuntu, NTFS if you want Windows to access it too, FAT32 for older versions Windows and some other OSs.

---

### Post by darkod on 2010-01-20
Neither. NTFS and FAT32 are windows filesystems.
Ubuntu is installed on ext4 filesystem by default, although you could use others, but not ntfs.
Just leave the space on your hdd that you plan for ubuntu as unallocated unpartitioned space (not belonging to any partition), and during ubuntu install select either Use Largest Available Free space or manual partitioning to set up ubuntu in that space.
DO NOT create any partitions from windows as it will be ntfs and thus useless.

PS. The above is for the ubuntu system partitions. If you are asking about a partition that you plan to share between windows and ubuntu, then ntfs is what you want.

---

### Post by wojox on 2010-01-20
You want ext4 or ext3 depending on which release tou have

---

### Post by caravanman on 2010-01-21
Not sure what ext4 abd 3 are.
Tried formating using fat32 
the problem I have is every time I try to install Ubuntu I get about half way through and the pc freezes. Tried all sorts of ways to get it to work. Its as though it times out.
I thought it might be the hard drive I dont think it is that now.

---

### Post by darkod on 2010-01-21
> **caravanman said:**
> Not sure what ext4 abd 3 are.
Tried formating using fat32 
the problem I have is every time I try to install Ubuntu I get about half way through and the pc freezes. Tried all sorts of ways to get it to work. Its as though it times out.
I thought it might be the hard drive I dont think it is that now.

ext is filesystem used by some linux distributions and ubuntu. First there was ext2, then ext3 and the latest ext4.
But it seems you have different problem. Don't worry about the filesystem, just leave that part of the hdd as unallocated unpartitioned space, and ubuntu installer will create the default ext4 filesystem. Even if you create ext4 partition in advance, you still need to use manual partitioning during install and tell it how to use the partition, which might be confusing if you haven't done it before. Linux doesn't work exactly like windows and preparing partitions in advance is different.

---

