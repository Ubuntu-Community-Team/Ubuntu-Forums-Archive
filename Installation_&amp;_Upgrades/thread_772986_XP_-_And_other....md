---
title: "XP - And other..."
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by akroev on 2008-04-28
Sorry if this is the wrong group to ask, but it's the one group that seemed least likely to be off-topic.

I'll explain:

I am about to buy a new laptop, which will be infected with Windows XP. I have not used MS systems on a box of mine since somewhere around 1995, when I had a copy of Windows 3.11 going. For reasons of compatibility, I want to keep XP on the box, so I can handle things like screen calibrations and firmware updates (assuming these are needed). However, I am not going to use the stuff, if I can avoid it.

So, my questions about this are:

1. How many GB should I let XP keep ? (The likely harddisk size will be on the order of 250 GB.)

2. Do I need to do anything from inside XP in connection with reducing the size of the filesystem(s) and the partition(s) ? If so, what ?

3. In a worst-case scenario, where I actually have to _use_ the damned thing, is it practical to let it use, say, an external harddisk for extra storage (avoiding the problem of resizing partitions for transitory situations) ?

TIA!
-akr
(linux user, allergic to MS)

---

### Post by pytheas22 on 2008-04-28
1. I've run XP on as little as 1.8 gigabytes, although since you have a decent-sized hard drive, I'd give it about 10 just to keep it happy and avoid stupid bubbles about being "critically low" on disk space as a result of Windows auto-downloading space-wasting garbage that no one needs.  This is assuming of course that you are only talking about a default XP install; if you are planning on also installing sizeable applications, you need to take that into account.  But if you are only going to use XP for firmware updates, there should be no reason for more than 10 gigabytes maximum.

2. no; Ubuntu/lots of other live CD's are capable of modifying partitions as needed.  But if you install XP on the hard drive first, just create a partition then of 10 gigabytes, leaving the rest unallocated, and you won't have to modify the XP partition at all.

3. sure, you can use an external drive for data storage and could even install Windows applications on it if necessary.

---

### Post by xzero1 on 2008-04-28
I keep the xp partition a bit under 5Gig so that I can back it up on a single dvd. I have other partitions formatted for xp storage though. I install everything to these other partitions.

---

