---
title: "gparted and the extended partition"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by pwabrahams on 2011-03-18
I'm trying to recover the space following the extended partition, which is currently unallocated.  I thought I could do that by having gparted enlarge the extended partition, but that option is greyed out.  Is there a way to do this with gparted?  Or, for that matter, with anything else?

---

### Post by cbowman57 on 2011-03-18
Are you using GParted from a live CD or the Gparted ISO?  If not that may be your problem.

---

### Post by oldfred on 2011-03-18
The liveCDs mount swap to speed things up a bit. But if swap is in the extended partition the entire extended is in effect mounted as it is one of the four primaries. 

You can right click on swap in gparted and swapoff.

---

### Post by cbowman57 on 2011-03-18
I didn't know that.  Good tip oldfred.

> **oldfred said:**
> The liveCDs mount swap to speed things up a bit. But if swap is in the extended partition the entire extended is in effect mounted as it is one of the four primaries. 

You can right click on swap in gparted and swapoff.

---

### Post by pwabrahams on 2011-03-18
I'm running a system on a memory stick, which is in effect, I think, a live CD.  The drive I'm repartitioning is a hard drive.  So problems with the swap partition are unlikely to account for my problem in enlarging the extended partition on /dev/sda.

---

### Post by Quackers on 2011-03-18
Please post a screenshot of the gparted window.

---

### Post by oldfred on 2011-03-18
The little key symbol shows if a partition is mounted or not. So that will tell if it is mounted.

---

### Post by Hedgehog1 on 2011-03-18
> **pwabrahams said:**
> I'm running a system on a memory stick, which is in effect, I think, a live CD. The drive I'm repartitioning is a hard drive. So problems with the swap partition are unlikely to account for my problem in enlarging the extended partition on /dev/sda.
 
The way to tell is to right click on the swap partition on the hard drive. If the option is SwapOff, that means it grabbed the swap.
 
This gets most folks as the swap on the HDD is often grabbed by the OS; please check it.
 
Once the swap is off, the expansion will be possible.
 
***The Hedge***
 
:KS

---

### Post by pwabrahams on 2011-03-19
I invoked swapoff on the swap partition on /dev/sda, and indeed the extended partition was freed up.  I then was able to expand it.

What misled me was that I never told the OS about /dev/sda, so it never occurred to me that the OS would unearth and use a swap partition on /dev/sda.  Damned clever!!

I wasn't sure whether leaving the swap partition off would affect it once I went back to running from /dev/sda again, so I turned it back on again. But I'm curious as to whether that was necessary.

---

### Post by Hedgehog1 on 2011-03-19
The swapoff is reset on reboot; but turning it back on is never  harmful.

The grabbing of any swap that happens to be available has caught us all off guard once ***or seventeen times***. It makes sense from an OS perspective; but it another step to remember in a year when you change partitions again...

***The Hedge***

:KS

---

