---
title: "Merging Partitions"
date: 2012-06-01
forum: Installation &amp; Upgrades
---

### Post by ExSuSEusr on 2012-06-01
Did a quick search and didn't see anything that could answer my question, so I thought I'd try here.

Have an older gaming system (laptop) ASUS G60V. 

Running Windows 7 on one partition and 12.04 on the other.

Decided to get rid of Windows.  Want to merge the partition into one.

In the process of creating a recovery disk for the Windows partition (just in case, you never know - only costs a few blank DVDs).

I have been playing around with trying to do this on my desktop - that is merge partitions into one, but haven't had much like.  I get end up with a formatted "Storage" drive.  

Any ideas on how to do this properly?  Again I am not looking for two separate drives here.

Simply what I want to do is the following:

Currently - Linux on one 150 gig partition // Windows on the other 150 gig partition.
Format over Windows and combine the partitions so that I end up with a 300 gig drive all Linux.  

Thanks

---

### Post by ExSuSEusr on 2012-06-01
Hmm I found gparted - but perhaps it might just be easier to do a fresh and clean install.....

---

### Post by wilee-nilee on 2012-06-01
> **ExSuSEusr said:**
> Did a quick search and didn't see anything that could answer my question, so I thought I'd try here.

Have an older gaming system (laptop) ASUS G60V. 

Running Windows 7 on one partition and 12.04 on the other.

Decided to get rid of Windows.  Want to merge the partition into one.

In the process of creating a recovery disk for the Windows partition (just in case, you never know - only costs a few blank DVDs).

I have been playing around with trying to do this on my desktop - that is merge partitions into one, but haven't had much like.  I get end up with a formatted "Storage" drive.  

Any ideas on how to do this properly?  Again I am not looking for two separate drives here.

Simply what I want to do is the following:

Currently - Linux on one 150 gig partition // Windows on the other 150 gig partition.
Format over Windows and combine the partitions so that I end up with a 300 gig drive all Linux.  

Thanks

Merging is actualy incorrect, you will just delete the Windows and resize the Ubuntu into the unallocated space.

Do this from a live Ubuntu cd with gparted with all partitions unmounted. 

There is usually a extended wrapped around a partition or partitions, you have to resize it first to resize a logical partition inside.

Post a screen shot of gparted if needed.

---

