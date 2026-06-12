---
title: "Partitioning/installation advice for new dual-boot system"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by twin_57103 on 2008-03-23
I'm building a new dual-boot system to replace one that is failing.  I'll be using Ubuntu and Windows Vista with two 320 Gb SATA hard drives (640 Gb total).  My though was to put Windows on all of one drive and split the other equally between Ubuntu and a data partition (NTFS).  Any thoughts about distribution?

Also, what is the best way to go about installing the operating systems?  I've installed Ubuntu several times (both dual-boot and as the sole OS) and various versions of Windows from 98 to XP, but this will be my first experience with Vista.  From what I've seen in the past, it seems like it would be best to start with Vista and add Ubuntu once Vista is set up.  Any thoughts?

Thanks!

---

### Post by Ub1476 on 2008-03-23
If I were you, I would first install Vista onto HDD1, then Ubuntu on HDD1 as well, and use HDD2 as storage. In Vista, there's a partition manager where you can give some GB to Ubuntu, and upon install, let Ubuntu use "free space available". 

The Ubuntu partition doesn't require more than 15-30GB if you store all music, movies, pictures on HDD2.

---

### Post by forestpixie on 2008-03-23
I'd almost agree - but I'd get gparted and make the partitions before I started - then you don't have to be resizing partitions - just make sure that the vista partition is first on the disc.

I believe that the problem with resizing vista partitions is where anexisting one is resized - so if it doesn't know about the ext3 partition it won't cause a problem - at least that' what I'd do if it was me.

---

### Post by twin_57103 on 2008-03-23
What is the advantage in putting both operating systems on one drive?  I am skittish about hardware failures because I've had so many things go wrong in the past.  When I had a hard drive fail in my current machine, having Windows on a separate drive saved my bacon - Ubuntu crashed, but I was able to use Windows as a stable OS for data recovery & diagnostics.  Will the second drive do better because of decreased use?

---

