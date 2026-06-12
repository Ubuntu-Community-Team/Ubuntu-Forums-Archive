---
title: "I'm a bit confused about primary/logical partitions"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by XmaX on 2008-01-25
I thought that partitioning would be easy, but that might not be the case. I already have 2 NTFS partitions, one with Vista. I want to shrink the second one, and install Ubuntu over there (so another 2 partitions). That would be fine, as that would total 4, so that I can set up my Ubuntu partition as primary. However, I discovered that I have an EISA 1.6 GB partition on my computer, don't know what that is. That means, that I have to make one of the partitions extended/logical. But, as far as I know, that requires continuous space, and that won't be achieved by Vista partition shrinking, would it?

---

### Post by v1cho on 2008-01-25
> **XmaX said:**
> But, as far as I know, that requires continuous space, and that won't be achieved by Vista partition shrinking, would it?
Kinda misunderstood this one... When you shrink the partition you will get some unallocated (not fomatted) space. Then you can format the unallocated space as an extended partition and create inside it  as many as you need.

---

### Post by StooJ on 2008-01-25
The hidden 1.6GB partition is probably some kind of manufacturer's recovery partition.

As V1cho said, when you shrink the NTFS partition (defrag first) you can create an extended partition in all the available room.

Then you create logical partitions within the extended partition. You need an extended partition for the  logical partitions to live in.

---

### Post by rmcder on 2008-01-25
You may have an additional problem here...  You apparently have 2 primary partitions already.  Adding the Ubuntu gives you a third.  Adding an extended (in which to install logical partitions) gives you a fourth...BUT...If you have a hidden recovery partition, or one for suspend/hibernate, that MAY also be a primary!  If it's a primary recovery partition, you can make a disk image backup and blow it away.  If it's a suspend/hibernate primary partition, you may not have that option.  Just something to check out.

---

### Post by XmaX on 2008-01-25
> **rmcder said:**
> You may have an additional problem here...  You apparently have 2 primary partitions already.  Adding the Ubuntu gives you a third.  Adding an extended (in which to install logical partitions) gives you a fourth...BUT...If you have a hidden recovery partition, or one for suspend/hibernate, that MAY also be a primary!  If it's a primary recovery partition, you can make a disk image backup and blow it away.  If it's a suspend/hibernate primary partition, you may not have that option.  Just something to check out.
Well, that's exactly what I thought. I'm pretty sure it's not a recovery partition, there is no receovery option during startup, and Toshipa supplied the laptop with a recovery DVD. So it has to be something else. 

Also, can't I just create an extended partition out of some space on my second partition? That would mean I have a primary recovery (or whatever it is) partition, primary Vista partition, primary NTFS partition and an extended partition for Ubuntu (which I can then divide for two logical partitions - one for Ubuntu, and the other for swap - even though I guess I don't need swap, I've got 2 GB of RAM, so I should be fine). That adds up to four, so it seems it would work, right?

---

### Post by StooJ on 2008-01-29
Linux needs a swop partition, regardless of your RAM.

Windows needs something similar as well, but uses the same partition as the OS (by default).

Not sure about installing Ubuntu on a logical partition, but it's worth a try. Make sure to backup your files first though, of course.

---

