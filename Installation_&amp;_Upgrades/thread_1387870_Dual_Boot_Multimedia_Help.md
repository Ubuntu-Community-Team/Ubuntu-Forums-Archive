---
title: "Dual Boot Multimedia Help"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by brian_utd7 on 2010-01-22
Hey guys, I have a question about dual booting windows 7 and ubuntu 9.10. What I want to be able to do is store my multimeda and open office files on a partition that can be read by both windows and ubuntu, I just don't know how to do this. What kind of partition should I make it? Should it be done in windows 7 or ubuntu?

---

### Post by Annigma on 2010-01-22
Hi :)
My PC is set up the way you want. Some of the kind folk from here helped me do it in [this thread here]("http://ubuntuforums.org/showthread.php?t=1321649") which might be helpful to you. 
Good luck

---

### Post by oldfred on 2010-01-22
If you have to resize your windows partition make sure you do it with the win7 tools inside windows and make sure it boots to be sure it is happy with the new size before you do other partitions.

Then you can use win7 or gparted to create new partitions. If you are sharing with windows, I recommend NTFS, as FAT cannot have files over 4GB and FAT is not journelized so it cannot recover as easily from file errors.

---

