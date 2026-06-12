---
title: "Is a swap partition required?"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by Christian Lindberg on 2008-06-28
Is it? I've got 3Gb of RAM so I got some to spare, because I've ran out of the maximum amount of primary partitions on the hard drive and this is make or break for me, secondly will the LiveCD for 8.04 complain about not having a swap?

---

### Post by housam on 2008-06-28
for normal use you only need about 1GB of swap . but if you'll going to hibernate or use heavy graphic programs , you'll need swap = RAM

---

### Post by Christian Lindberg on 2008-06-28
Nah, I'm going to use Ubuntu for other things then 3D heavy stuff, got Windows for that, also I use sleep, not hibernation, I feel my laptop can survive :)

---

### Post by housam on 2008-06-28
Ok then, do create a small swap partition . 1 GB is ok.

---

### Post by avtolle on 2008-06-28
To add a swap partition, the OP will need to change one of the primary partitions to an extended partition, and within the extended partition create a logical partition for the swap partition. [https://help.ubuntu.com/community/forum/installation/Partitioning](https://help.ubuntu.com/community/forum/installation/Partitioning) contains some general useful information on partitioning a HDD in Ubuntu.

---

### Post by ramadan on 2008-06-28
am new to Linux but I've read that you can use the same way of windows(pagefile.sys) i.e. you don't need to make a swab partition
don't ask me how but if you concerned do some research
good luck

---

### Post by housam on 2008-06-28
> **ramadan said:**
> am new to Linux but I've read that you can use the same way of windows(pagefile.sys) i.e. you don't need to make a swab partition
don't ask me how but if you concerned do some research
good luck
You are right. you can create a swap file instead of a swap partition . and both do the same functions. read about it [[COLOR="Red"]_here_[/COLOR]]("https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?").

---

