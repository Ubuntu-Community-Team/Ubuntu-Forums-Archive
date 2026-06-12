---
title: "Dual boot install issue with partitioning."
date: 2012-04-17
forum: Installation &amp; Upgrades
---

### Post by aerinthaare on 2012-04-17
I have recently purchased an Alienware M14X laptop, for gaming, and I am not entirely ready to switch it completely to ubuntu. Unfortunately, every time I attempt to dual install, I get an incompatibility issue between the OS partitions. I would like to be able to test everything to make sure it all works properly before finalizing the switch, however, I also want to avoid having to double the space taken on my HD. Does anybody know how to manage this?

---

### Post by darkod on 2012-04-17
You are trying to use the same partition as system partition for both OSs?

Very rarely possible, if at all.

For a quick try, you don't have to give ubuntu too much space. If you don't plan to start guarding large files (it's only a test run), you can give it as much as 10GB only. If you already have a swap partition it can use the same one.

Laptops these days come with huge disks, you can't spare 10GB?

---

### Post by aerinthaare on 2012-04-17
What i am trying to accomplish hear is; a partition for each OS, and a separate partition for data. Such that all of my files are accessable to both OS's.

---

### Post by darkod on 2012-04-17
So what exactly is the problem?

Sounds good, just make sure the data partition has a filesystem that both OSs can read/write.

---

### Post by aerinthaare on 2012-04-17
I have tried this on another computer, and I can never seem to get crossover partition access to work properly. Could direct me to the location of a good tutorial to partitioning? I am not sure where the most credible can be found.

---

### Post by Mark Phelps on 2012-04-18
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by oldfred on 2012-04-18
Often users that have issues with dual boot, is because they hibernate in Windows and then write something into Windows from Ubuntu and of course hibernation then does not know about it and messes up system.

Best to not hibernate with dual boot. Also best to always use a shared NTFS partition for read/write and set Windows system partition as read-only to avoid issues. Ubuntu does not hide vital Windows system files like Windows does and makes it too easy to corrupt system if one is not very careful. I used to always show all files when booted  in Windows, and would occasionally click/drag a vital folder to a new place.

---

