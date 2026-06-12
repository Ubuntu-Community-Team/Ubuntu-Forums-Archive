---
title: "[SOLVED] Dual boot Vista - Ubuntu 7.04 on a Toshiba A100"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by bhubesi on 2007-09-10
I have been using Ubuntu for a year. Today I got a new computer. It comes with Vista Home Premium pre-installed. Though I normally do not use Windows I'd like to keep it. Now I need to install Ubuntu 7.04

I found out in the forums that Vista comes with a tool that allows you to resize your partitions. I went for it. 

The disk already comes with "Vista C" and "Data E". It means I need to resize both. Now:

1. Why can't I resize as much as I want? In a disk of 120 Gb I will only allow 51 Gb for Ubuntu (when I hardly use Windows). Is there any other way?

2. I will remain with two partitions of 24 Gb and 27 Gb. How do I put them together?

---

### Post by merlinus on 2007-09-10
You do not need to put them together.  You can resize one for /, /home and /swap, and use the other for data.

---

### Post by bhubesi on 2007-09-11
Thanks for the idea!

Once I had a machine with XP and Ubuntu. Just one partition and I could decide what to give to each one. I guess I am not enthusiastic about having four partitions and giving that much to Vista...

---

### Post by merlinus on 2007-09-11
Before attempting ubuntu install, delete temp and other unneeded files, backup data, set virtual paging to zero (set it back after install), and defrag several times.

Then use vista's disk manager to resize its partition.

---

### Post by bhubesi on 2007-09-11
Thanks a lot. I have just solved it. 

As the computer was new and no data had been inserted, I just deleted the E partition (for data), resized C to 40 Gb and left 70 unallocated. (I did this from "computer - manage - disk".

Then I booted from the cd of Ubuntu 7.04 and allowed it to install automatically in the largest free space. 

It was perfect. No problem at all.

---

### Post by merlinus on 2007-09-11
Well done, and good luck!

---

