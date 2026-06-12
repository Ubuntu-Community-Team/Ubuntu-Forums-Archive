---
title: "Need helping juggling partitions during installation"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by ERAUman on 2008-06-03
Just as a forenote I did a quick search and could not find helpful information.  

I want to install Ubuntu 8.04 (already have the CD) and I have 3 hard drives (40,80,500GB) with winXP on the 80gb. I want to install ubuntu on the 500gb hdd on a small partition.  What is the best way to partition my drives?  I've read that ubuntu works with ntfs so it seems that the best solution would be to install ubuntu on a small partition (~5gb) and leave the rest of the 500gb as NTFS. I guess my questions are; What is the smallest partition I can create on my 500gb hdd, what software should I use (as the software on the ubuntu installation cd seems like it's going to require me to completely redo all of my partitions), and what should I be careful to not do so I won't lose all of my data?

---

### Post by KingTermite on 2008-06-03
Here is a partitioning scheme that a fellow forumite wrote:
[http://boomerclan.info/index.php/Linux/Building-a-Grub-Boot-Loader-in-a-Dedicated-Partition.html](http://boomerclan.info/index.php/Linux/Building-a-Grub-Boot-Loader-in-a-Dedicated-Partition.html)

As far as size.....if you have 500Gb, why are you so worried about making it the absolute smallest partition you can? Surely you can afford a little extra room so that you can install a few packages after installation if you wish to, etc... I'd give it 20Gb and ensure I had plenty of extra room (that's still only 4% of the drive's size).

---

### Post by ERAUman on 2008-06-03
> **KingTermite said:**
> Here is a partitioning scheme that a fellow forumite wrote:
[http://boomerclan.info/index.php/Linux/Building-a-Grub-Boot-Loader-in-a-Dedicated-Partition.html](http://boomerclan.info/index.php/Linux/Building-a-Grub-Boot-Loader-in-a-Dedicated-Partition.html)

As far as size.....if you have 500Gb, why are you so worried about making it the absolute smallest partition you can? Surely you can afford a little extra room so that you can install a few packages after installation if you wish to, etc... I'd give it 20Gb and ensure I had plenty of extra room (that's still only 4% of the drive's size).
Thanks for the quick response and the link. I'll go with alloting 20gb of hdd space for ubuntu.

---

### Post by ERAUman on 2008-06-03
Ok, I've run into a pretty big problem.  I decided to install ubuntu onto my 40gb hdd and it works fine (still trying to get the dual monitors up though).  But now winXP will not boot, and I didn't do anything to the hdd that it was on (the 80gb one). If it helps at all, i have my 40gb as the first master hdd and the 80gb is the slave and the 500gb one is the second master. When I try to boot XP it gives me an "Operating system error".

---

### Post by ERAUman on 2008-06-04
I have one more quick question.  I accidentally unmounted a harddrive before I shutdown ubuntu.  How do i retrieve it?

---

