---
title: "Lost Free Space on Partition Table"
date: 2016-01-22
forum: Installation &amp; Upgrades
---

### Post by martin188 on 2016-01-22
I have created 9GB of free space in my Windows c: partition by shrinking the partition.
   
  Attempting to install Ubuntu, in the ‘Something else’ option, I am trying to allocate the free space as 7GB to the Root partition and 2GB to Swap.
   
  The problem I am having is that once I allocate the 7GB, the remaining 2GB goes missing. I expected to see 2GB of free space remaining on the Partition Table, but there is nothing left to allocate to Swap?

---

### Post by Vladlenin5000 on 2016-01-22
Hi and welcome.

Can you provide a screenshot showing that weirdness you just described?

---

### Post by martin188 on 2016-01-22
Will do (a bit later), I assumed it would be something obvious.

Thanks

---

### Post by ajgreeny on 2016-01-22
You may already have the 4 primary partitions that are available in an MBR BIOS mode partition table, though I would still expect the free space to show as unallocated.

As mentioned below, a screenshot from gparted which is in your install DVD or USB would be very useful.

---

### Post by martin188 on 2016-01-23
According to Macrium Reflect my Disk is GPT. It already has 4 primary partitions, not sure if this matters with GPT?

Following shortly are the Partion Table images.

[ATTACH=CONFIG]266897[/ATTACH][ATTACH=CONFIG]266898[/ATTACH][ATTACH=CONFIG]266900[/ATTACH]

---

### Post by martin188 on 2016-01-23
Sorry, I just realised that I need to scroll down, problem resolved.

Does anyone agree/disagree with my allocation of 7GB Root, 2GB Swap? I have 2GB RAM. I can't spare any more than 9GB disk space.

---

### Post by oldfred on 2016-01-23
If system has only 2GB of RAM, you may not be able to run standard Ubuntu. And that may be more the video chip/card you have.
I do have full 12.04 on my old laptop from 2006 but have to run gnome-panel/fallback as Unity just requires too much video horsepower and old chip does not have it.
May be better with Lubuntu. Should be a bit smaller also as 7GB is not large, you will have to regularly houseclean. Same with Windows as you must regularly houseclean.

---

