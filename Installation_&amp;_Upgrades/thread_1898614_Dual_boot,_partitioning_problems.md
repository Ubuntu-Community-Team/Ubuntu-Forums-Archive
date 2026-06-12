---
title: "Dual boot, partitioning problems"
date: 2011-12-21
forum: Installation &amp; Upgrades
---

### Post by theskag on 2011-12-21
Hi, 
I could not find a thread regarding something like this.

I have an SSD with GPT and I'm trying to dual boot Windows 7 and Debian.
Problem is after installing Windows, Debian see the harddrive as fully unallocated.
I cannot install Debian without replacing Windows along with it's partitions.

I've tried to partition with a live cd and then try to install. Problem is then that 
the Windows installation refuses to install on that partition or to create a new one.

Same thing happens with Ubuntu.
Where do I go from here?

Any help appreciated,

---

### Post by darkod on 2011-12-22
Usually from what I have seen the disk is shown as unallocated if there is an error in the partition table. Windows often ignores these errors so just because windows works does not mean all is fine.

Double check the partitions, start and end sectors (there is no overlapping), etc.

Make sure you don't have RAID enabled in bios or raid meta data on the disk if it was used in RAID before (formatting doesn't remove this).

---

