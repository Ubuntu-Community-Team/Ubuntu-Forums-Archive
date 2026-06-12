---
title: "Ubuntu doesn't see my partitions"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by Mr Tim on 2007-07-04
I want to dual boot Ubuntu 7.04 with XP (not ready to change fully... yet), but I have encountered problems in the installation process. I load up the live CD, press install, go through the first few steps, then when it gets to step 4 "prepare disk space" it only gives me the "manual" option. When I click forwards it doesn't show any partitions. I made a split my C drive into two partitions in partition magic, leaving some for Windows C drive and about 100 Gig for Ubuntu (I also have a third recovery partition). I've tried numerous file systems for the second partition but none of them show up in the installer:(.
Any help would be greatly appreciated.

---

### Post by Analord on 2007-07-04
Make a partition, don't make filesystem
Just unallocated space, and 'tell' ubuntu to install there.

---

### Post by Mr Tim on 2007-07-04
I've already tried that and it didn't work. :cry:

---

### Post by robert@debian on 2007-07-04
Can you please tell us how your partition table looks like?

**START**|--Windows formated with NTFS--||--another partition with NTFS formated--||--recovery partition with FAT32--| **END** (no space left on the HDD)

Does the installer show any partition at all? Your HDD is recognised by Ubuntu right?

---

### Post by Mr Tim on 2007-07-04
The installer shows no partition, the partition table looks pretty much what you said (with the middle partition having various file systems throughout its short life, currently unallocated).
I'm not sure if Ubuntu recognizes my HDD.

---

### Post by robert@debian on 2007-07-04
You could check it with **qtparted**, afaik it comes with the Ubuntu liveCD.
It's a partition manager just like Partition Magic.

Is your HDD connected via S-ATA?

---

### Post by Mr Tim on 2007-07-04
Nothing is coming up on Gparted (it says "no devices detected"). I'm quite sure that my HDD is connected via SATA (that is about the extent of my knowledge on the subject)

---

### Post by robert@debian on 2007-07-05
Sorry, I've kept you waiting.

The kernel obviously does not support your SATA controller. The problem is, that my knowledge 
with SATA Controllers is very limited ;-(

I would try to figure out what SATA controller you have. Check your mainboard manual for example.
And then try to find any threads on ubuntuforums about this problem. I'm pretty sure you are not
the first with this problem.

---

