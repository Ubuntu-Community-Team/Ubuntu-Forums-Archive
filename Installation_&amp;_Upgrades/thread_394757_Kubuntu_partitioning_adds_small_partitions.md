---
title: "Kubuntu partitioning adds small partitions"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by eidauk on 2007-03-27
Linux newbie. I'm installing Kubuntu at the end of my 40 GB HD. Dual-booting with Windows on the first 30 GB. However, during installation and manually editing the partition table, it keeps adding a small secondary partition (about 2 GB) between my windows partition and the one I just created. If I then create another partition it again adds another small partition. I only want these partitions:

- Windows
- Linux swap
- Linux root
- Linux home

But at this rate I'll end up with EIGHT partitions! What's going on? Why does it create this smaller partition.

---

### Post by Big_Croc7 on 2007-03-28
Two explanations/options:
1- what are these 'phantom' partitions called? If it's something like hda1-1, then it's free space - that's simply the label QTParted (the partitioning tool) gives it.  In that case, it's not adjusting the size of the new partitions correctly (or you're not); try creating one partition in the last 10Gb and see if the issue is still there.
2- it could be a bug in QTParted (the partitioner used in Kubuntu), I've found it can be a bit problematic.  Try partitioning your disk first, before the install, with the GParted liveCD - it's a CD that boots just for partitioning, and I'd recommend having one around anyway.

---

### Post by eidauk on 2007-03-28
Thanks for the response. I can't remember what they are called but it does say "free". I gave up on QTparted and used the partition program that is on the Ubuntu live CD (I believe that's Gparted) and it worked perfectly. Then I installed Kubuntu.

---

