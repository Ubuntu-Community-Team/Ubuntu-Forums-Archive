---
title: "Free up partition"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by victor_sk on 2011-06-19
Hi everyone,

My partition architecture is such that it has 4 primary partitions.  I have 70GB of unallocated space but I cannot create a new primary partition anymore.  

My gparted information shows "System Reserved" NTFS partition.  I don't use any Windows at all, just Ubuntu and openSUSE.  This "System Reserved" partition seems to be the first one with beginning sectors but it is my Ubuntu partition that delegates the bootloader.

Do you think that if I delete the "System Reserved" partition nothing catastrophic will happen or should I better not delete it?

Thanks,
Victor.

---

### Post by Quackers on 2011-06-19
Is this partition 100MB to 200MB in size and of NTFS type?
If so, and you definitely have no Windows system on the pc it will be safe to delete it.

---

