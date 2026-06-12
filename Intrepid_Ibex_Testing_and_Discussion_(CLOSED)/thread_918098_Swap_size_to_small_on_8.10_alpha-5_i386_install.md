---
title: "Swap size to small on 8.10 alpha-5 i386 install"
date: 2008-09-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bentledr on 2008-09-12
I have recently installed 8.10 alpha-5 i386 on a spare drive in my main machine using guided partitioning use entire disk (disk size 40 gig) and noticed that the swap partition was rather small compared to the one used in 8.04.

In 8.04 the swap partition on a 160 gig disk was 6.3 gig and with 8.10 alpha-5 it is only 1.6 gig on a 40 gig disk.

The machine has 4 gig of ram so swap hardly ever gets used but doesn't it need to be at least the size of available ram if it is used to store a memory image when the system is hibernated.

System monitor shows available ram of 3.5 gig so to be on the safe side in case you upgrade to a PAE capable kernel which on this machine gives an available ram of 3.8 gig the default swap of 1.6 gig is somewhat under sized.

Can someone confirm my assumption that the swap should be at least the size of potentially free memory or has the way hibernation is done been changed between 8.04 and 8.10.

---

### Post by BCurtisWX on 2008-09-12
> **bentledr said:**
> I have recently installed 8.10 alpha-5 i386 on a spare drive in my main machine using guided partitioning use entire disk (disk size 40 gig) and noticed that the swap partition was rather small compared to the one used in 8.04.

In 8.04 the swap partition on a 160 gig disk was 6.3 gig and with 8.10 alpha-5 it is only 1.6 gig on a 40 gig disk.

The machine has 4 gig of ram so swap hardly ever gets used but doesn't it need to be at least the size of available ram if it is used to store a memory image when the system is hibernated.

System monitor shows available ram of 3.5 gig so to be on the safe side in case you upgrade to a PAE capable kernel which on this machine gives an available ram of 3.8 gig the default swap of 1.6 gig is somewhat under sized.

Can someone confirm my assumption that the swap should be at least the size of potentially free memory or has the way hibernation is done been changed between 8.04 and 8.10.

Based on the fact that 1.6 is 4 times lower than 6.4 and 40GB is 4 times lower than 160GB.  I would say its meant to do that.

---

### Post by jmcvey on 2008-09-14
Can't confirm what the size should be aside from my experience. I have a laptop with a current Hardy 64-bit install. Swap is set to a bit over 4GB on that even though it is rarely used. That size was set mainly to support hibernation (I've got 4GB on the laptop).

Went ahead and opened some space at the end of the drive to put a test Intrepid setup on the same box. I let the installer for Intrepid configure the space and it setup a swap partition that was only around 1GB or so. Thought that strange but left it. However, when I tried to test hibernation it failed with a message about the storage space was too small to support the hibernation image. Well, went into fstab and pointed swap to the other swap partition on the drive (the one for Hardy since I'm not running both at the same time) and then tested. Hibernation worked fine that time.

So, I think the default settings Intrepid picks are fine for running the machine, but does not consider what is needed for the hibernation file. If you really need to hibernate, you'll most likely have to manually setup the partitions or run gparted to resize them.

Jer

---

### Post by Gina on 2008-09-14
As I recall, twice RAM is recommended but with 4M RAM already it might be different.

---

### Post by bentledr on 2008-09-14
Its not just me then there would seem to be a bug in the routine in the installer that decides on swap file size if it bases its decision on installed memory size but it may be doing it as a fixed percentage of partition size as in 8.04 on a 30 gig disk with 512 meg of ram the swap is 1.2 gig or about 4% of the disk space and now 8.10 seems to be obeying the 4% rule with 1.6 gig on a 40 gig drive.

Can someone confirm how the swap partition size is decided when you let the installer do guided use entire disk or guided having created free space.

Is it just a fixed percentage of available disk space or does it take into account the amount of usable memory in any way.

How big is your laptop hard disk and how much free space did you let the installer create.

---

