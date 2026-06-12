---
title: "What gives with the imac partition?"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by DirtDawg on 2006-09-23
I'm replacing my Ubuntu with Xubuntu (Dapper) on my imac today and decided to partition manually, as the default partition creates a smaller-than-desired swap.

I had used the automatic install before, so the partitions were already set up. They looked like this:

#1 32.3kb Apple <-- Makes sense not to mess with this one
#2 1.0 B K Boot untitled
#3 9.8 GB **K** ext3 **/media/untitled**
#4 455.9 MB F swap swap

So I repartitioned the swap to a larger size, but was confused with the ext3 partition. I thought I should mount it at "/", but seeing it was allocated to "/media/untitled", I figured maybe I should mimic that. It didn't work, tthe machine griped about no root partition(which makes sense). Here's the final setup(Apple and Boot partitions remain unchanged):

#4 9.6 GB **F** ext3 **/**
#3 628 MB swap

For the life of me, I couldn't figure out how to replace that F with the original K. I don't even know what that means or if it's important. I also assume mounting at root is the correct procedure, but why did the automatic install mount the ext3 partition at "/media/untitled"?

The system is installing now, but I'm curious why why why? Anyone have some insight?

---

### Post by K.Mandla on 2006-09-23
That's pretty weird. I don't know why that would happen, but I think the partitioner tries to sort out prepartitioned areas by size. I've noticed that building something like 

96Mb ext2
4Gb ext3
512Mb swap
4.1Gb ext3 

gets root assigned to the last and largest partition, with the rest going to /media/hda2, /media/hda3, and so forth. 

Don't know what the F/K is either. Hmmm. Google time.

---

### Post by DirtDawg on 2006-09-23
> **K.Mandla said:**
> That's pretty weird. I don't know why that would happen, but I think the partitioner tries to sort out prepartitioned areas by size. I've noticed that building something like 

96Mb ext2
4Gb ext3
512Mb swap
4.1Gb ext3 

gets root assigned to the last and largest partition, with the rest going to /media/hda2, /media/hda3, and so forth. 

Don't know what the F/K is either. Hmmm. Google time.

Well I'm writing this on the new system so it appears to be working fine. The odd partitioning may have something to do with imac g3's or ppc's in general(?) as [this]("http://www.ubuntuforums.org/showthread.php?t=190910&highlight=%2Fmedia%2Funtitled") fellow seems to have the same set up on his g3 with auto installer.

---

