---
title: "Ubuntu not recognizing my hard drives"
date: 2012-03-17
forum: Installation &amp; Upgrades
---

### Post by jbm715 on 2012-03-17
So I have a 240GB ssd, a 160GB 7200 hdd, and 2x1TB hdd in a hardware raid 1. I installed windows on the 240GB drive. I want to install ubuntu 11.10 on the 160GB drive. 

I downloaded the 11.10 alternate iso.  The installer recognizes that I have raid configurationm and asks if I'd like to active the raid. If I say yes or no, no drives are found to setup partitions on.

I tried putting the sata controller into ahci mode but that still didn't help.

GParted was able to locate the drives and their partitions just fine.

Where should I go from here?

---

### Post by darkod on 2012-03-17
If the 160GB disk has been used in fakeraid before, it has meta data leftovers. The installer will ignore it.

You can remove the meta data from live mode in terminal by:

MAKE SURE YOU USE THE CORRECT DEVICE /dev/sdX

sudo dmraid -E -r /dev/sd[COLOR=Red]X[/COLOR]

IMPORTANT: Since you have disks in fakeraid, make sure you use the above command on the correct disk. If you use it on any of your raid disks it will break your array.

Also, make sure you have the disk plugged into a port that doesn't belong to the RAID function. Usually only two ports are part of the raid function. If you have more on your board, you need the 160GB disk in a port without it.

---

### Post by jbm715 on 2012-03-17
Thanks for the reply.  Only the 2 1TB drives have been raided. I've never used fake raid before. None of my drives are recognized.

---

### Post by darkod on 2012-03-18
Usually the main issue when the disk or partitions are not displayed is the existence of meta data. That can be removed with that dmraid command.

As for fakeraid vs hardware raid, unless it's a dedicated raid card you have, using the BIOS raid is usually called fakeraid. Even some raid cards work on the fakeraid principle.

The point is the same, if the disk was used in raid earlier it might have meta data remains. Maybe it was used by you or someone else.

Apart from this, if there is an error in the partition table a disk might now be shown correctly but in your case none of them show, so that doesn't seem to be the reason.

Since you don't plan to install ubuntu onto the raid, you can also try installing with the standard desktop cd, it might work better.

---

### Post by NotebookNerds on 2012-03-18
> **darkod said:**
> Since you don't plan to install ubuntu onto the raid, you can also try installing with the standard desktop cd, it might work better.

I agree, this would be your best bet.

---

