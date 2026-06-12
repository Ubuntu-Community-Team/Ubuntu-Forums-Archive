---
title: "Flash drive fails - startup disk"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by palz2015 on 2010-02-25
I am trying to install Ubuntu Karmic on an 8G USB flash drive. I have formatted it many times. Here is what I do:

Open GParted, format it to ext4 (or any other  Linux FS), open USB Startup disk creator, and there is a /!\ next to /dev/sdd1 (that is ext4). And when I refresh gparted, it says "unknown" for /dev/sdd1 or sometimes FAT32. The USB startup creator fails and must be force quit many times.

I have had mounting issues with this device before. 
Can someone tell me a good FS to use (I try ext2,3,4, jfs, xfs, reiser4,FS, FAT32) or how to fix this issue?

---

### Post by spectralblue on 2010-02-27
You should use FAT32 if you're just making a live USB.

Do you have at least one partition? In the Startup Disk, does it say any free space in there? You have to click on the partition (the one with the Free Space) to install it there rather than the device itself. You can't install it to the one with the exclamation point because that is the device, rather than a partition.

---

### Post by palz2015 on 2010-02-27
Well, I have installed it on a FAT32 partition. It seemingly works. So now can I use it as an HDD and store files/ install packages on it?
(Being the n00b I am, I * installed* Ubuntu on that drive, and messed up my multiboot of windows 7 and ubuntu on my SATA HDD- I had to reinstall Ubuntu to fix the bootloader XD)

---

