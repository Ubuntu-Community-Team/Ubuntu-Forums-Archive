---
title: "Re-Installing Ubuntu 10.10 - which partition?"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by Enigmaman on 2011-06-28
Hi 

I am reinstalling Ubuntu 10.10 - the most up to date version which works on my computer. I plan to run a dual boot with Windows XP.

The hard disk is already partitioned and one of  the two biggest partitions is empty. I want to install Ubuntu on this partition. How can I make sure please that it goes on the correct partition? I am converned not to overwrite Windows. 

Meanwhile can I be sure that I will get GRUB boot menu installed? 

I am wondering, would it be wiser to merge the partition first and then install Ubuntu, letting the installation process create a partition afresh?

---

### Post by Mark Phelps on 2011-06-28
How did you do the partitioning?

If the "second" partition is NTFS, you can't use that to install Linux as it is an MS Windows filesystem.  

If the "second" partition is a Linux filesystem, you would do better leaving it as unallocated space and letting the Ubuntu installer do the formatting.

When you go to do the formatting, the installer will ask you which partition.  You can help avoid overwriting Windows if the two disk areas are very different sizes.  That will help you determine WHICH area is to be overwritten by the installer.

---

