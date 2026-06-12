---
title: "No Root - Partitioning Problems"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by biv on 2005-10-25
I have 3 partitions with windows xp as my first, then a ext2 and then a swap. I stuck the cd in, and went up to the part of partitioning the hard drives. The only opition it gave me was to format the entire drive, well I don't want that so I went to the manual part, made sure the second partition(ext2) flag was set to boot. 
I then say I am finished, where I then get the "No root file system is defined. Please correct this from the menu". Well I don't know what to do, so I switched the boot flag to NTFS, see if that worked. Same thing. 
In addition, I can't boot into windows anymore.
So now I am pretty lost and without a computer.

---

### Post by kairu0 on 2005-10-25
When you set up that second partition, specific a mount point called "/" (no quotes) for it. You do this on the same page as where you set up the boot flag.

A root partition is the lowest level directory in Linux. It's kind of equivalent to the necessary C: in DOS or older Windows.

---

