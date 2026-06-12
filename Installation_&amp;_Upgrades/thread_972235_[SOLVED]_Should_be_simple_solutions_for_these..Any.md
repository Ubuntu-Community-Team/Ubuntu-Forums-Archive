---
title: "[SOLVED] Should be simple solutions for these..Anyone?"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by VastOne on 2008-11-05
1: Upgraded my 8.04 on my first SATA drive with very little issues and am happy with the install...So, to see if there was anything different at all from an upgrade to a clean install, I did a fresh install to my second SATA with the ISO disk. I had about 122 gig of storage on that drive so I let the install (gpart) repartition it and have a partition that is 122 gig with no space left, and the Ubuntu file system on the other partition. I also allowed a completely new grub and swap partition.

I am having major issues with this install, from Amarok crashing as it tries to read from the 122 gig of mp3 files, I am assuming it is a space issue. Amarok loads those same file without issue from the first disk upgraded version no problem.

In short, I want to scratch the 2nd SATA disk install completely, using gpart to format it. My concern is obvious, I want to go back to my fist disks grub...Can someone point me in that direction? Appreciate it.

Once I get that taken care of, I will create a new partition for \home of the first SATA Ubuntu and use it going forward, and reinstall using better options (manual instead of guided) on the 2nd SATA again.

2: 2nd computer. I had upgraded to the RC version and was quite pleased with the results. When the release came out, I appeared to have successfully upgraded to the full Ibex version with the exception of the Kernel. Instead of being at the expected 2.6.27-7-generic, I am still at 2.6.24-12 and uname -r confirms this. I saw Update Manager pull in 2.6.27-7-generic and it is in the \boot folder, but it is not loading or even put it in grub. 

Any thoughts on this?

VastOne

---

