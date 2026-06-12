---
title: "Cannot install 9.10, install freezes on partition."
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by Trifidlebock on 2010-01-19
i just built a new computer with:

AMD Phenom II X4 955 3.2GH
ASUS M4A785TD-V EVO 785G RT
4 GB of Mushkin Memory
    
I have tried to install Ubuntu on 3 different SATA harddrives and every time it freezes on install during the partitioning.  I have tried to manually partition and to erase the entire drive.  No matter what I do, it fails.  Windows 7 runs perfectly, but I much prefer to use Ubuntu whenever possible.

Hell, I even tried installing the Lucid alpha just to see if it'd make a difference.

What am I missing?  Any ideas?  I really really don't want to give up on Ubuntu, but I have spent like 15 hours on this reading and trying everything I can think of.

Thanks.

---

### Post by Trifidlebock on 2010-01-19
Also, more info.  G-Parted and the default Disk Manager Utility (or whatever its called) usually seem to be able to partition Fat32 fine.  Windows has no trouble partitioning anything.

I was able to get one hard drive partitioned with an Ext4 and Swap partition and then do the install without formatting a couple times.  In each case, the install was supposedly successful, but during the Ubuntu boot the screen would just blank out and the OS would never fully load.

The live cd boots Ubuntu fine.

---

### Post by confusedstingray on 2010-01-21
i had the same problem what fix mine was format the 910 partition to ext3 and things seem fine, still trying to use ext 4 like you  i have tried 5 drives all different sizes makes and partitions no luck. I think it might be a AMD 64 quirk or mb quirk still trying

---

