---
title: "Order of partitions for root, home and swap with respect to Windows partitions"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by flylehe on 2011-02-09
I am installing Ubuntu on the same hard drive as Windows 7.

The partitions of Windows 7 have already occupied the left part of the hard drive. From left to right, the Windows partitions are one partition for Windows booting, one for Windows OS and software installation, and one for data which is planned to mount on Ubuntu. 

I was wondering how to arrange the order of partitions of root, home and swap, i.e. which is on the left just besides one Windows partition, which is in the middle and which is on the far right? Is there some consideration regarding about this arrangement?

Thanks and regards!

---

### Post by bryanl on 2011-02-09
order of the partitions doesn't make much of a difference. the number of partitions does.

You can have only 4 primary partitions. If you need more than this, then you need to set up an extended partition with its sub partitions. (traditional MBR, not Apple or more modern GPT schemes)

If I've got 2 defined windows partitions, I just add a 12 to 16 GB partition for the Ubuntu root and use whatever free space is left on the drive for /home. I use a swapfile to avoid a separate swap partition (see [Move to swapfile rather than swap partition](http://tcl.leipper.org/2009/08/move-to-swapfile-rather-than-swap-partition-2/)).

---

