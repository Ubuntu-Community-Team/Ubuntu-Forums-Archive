---
title: "How can I safely resize partitions with a dual-boot setup running Karmic &amp; Windows 7?"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by mario0318 on 2009-11-18
I installed Windows 7 x64 and Ubuntu 9.10 x64 afterwards. I gave Ubuntu a set amount of space before the regular install. A drive of 240gb, with 180 for Windows and 50 for Linux. How could I safely resize the partitions to increase the size of the Ubuntu drive, as in reducing the size of Windows which has alot of free space (NTFS) and increasing the size for Ubuntu which is running ext4.

I would prefer not having to reinstall anything, much less my linux partition since I've yet to find a good backup utility that can make drive images. I got one for Windows but not Ubuntu. Any tips and help?

---

### Post by darkod on 2009-11-18
For the backup, take a look at CloneZilla. I haven't used it personally because I just started using Ubuntu too and didn't need linux backup solution. But I was reading about it the other day and it looks promising.
Plus there are packages in the Software Centre, maybe more experienced users can recommend some.
For shrink/expand Gparted is preferred. If you boot with the ubuntu cd and select Try Ubuntu that does not mount your hdd and you can play with the partitions. But I haven't used it to expand ext4, just to shrink ntfs, so you might wanna wait for second opinion how safe it is. I guess any partition changes carry some degree of risk. :)

---

### Post by dhavalbbhatt on 2009-11-18
> **mario0318 said:**
> I installed Windows 7 x64 and Ubuntu 9.10 x64 afterwards. I gave Ubuntu a set amount of space before the regular install. A drive of 240gb, with 180 for Windows and 50 for Linux. How could I safely resize the partitions to increase the size of the Ubuntu drive, as in reducing the size of Windows which has alot of free space (NTFS) and increasing the size for Ubuntu which is running ext4.

I would prefer not having to reinstall anything, much less my linux partition since I've yet to find a good backup utility that can make drive images. I got one for Windows but not Ubuntu. Any tips and help?

You will have to do a couple of things - 
1) Deframent your Windows partition using the Defragmentation tool in Windows. 
2) Resize your Windows partion - again, using the partition tool in Windows
Once you have created the free space that you want, you can then use GParted from a LiveCD environment to increase the partition size of your Ubuntu partition.

One note of caution though, Windows partition tool is pathetic and might not allow you to use all the free space that you may have on your Windows partition, so at the risk of loosing some data (maybe you can do a complete back up of your Windows partition), you may be better off with just using GParted from a LiveCD environment to resize your Windows partition. I would still defragment the Windows partition, just to be on the safe side.

---

### Post by camrant on 2009-11-19
I would like to resize partitions similarly, the difference is I want to reduce the size of my previous installation of ubuntu's partition and increase the size of 9.10's partition.  Rather than upgrade I wanted to try a fresh install but only allocated 6 gig to give it a try.  Now I want to move over to the new install.  Increase the new partition and copy files over to my new /home and then later give the whole drive to my new installation.

---

