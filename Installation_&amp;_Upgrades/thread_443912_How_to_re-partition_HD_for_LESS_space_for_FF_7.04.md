---
title: "How to re-partition HD for LESS space for FF 7.04?"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by intricate on 2007-05-14
How can I re-partition my 100GB laptop Hard drive to allocate less space to FF 7.04? I allowed the native Ubuntu FF 7.04 partitioner to select the amount of space to partition and it used almost 50Gb of my 100Gb hard drive. Can I reduce the 50Gb to some amount say 25 Gb using some utility or tool? Or, do I need to completely re-install FF 7.04 and reformat that partition?

Thanks to the experts who inhabit this forum and confer their knowledge and expertise upon beginners and novices such as myself.

---

### Post by ep2011 on 2007-05-14
Boot with the Feisty live cd (or gparted live cd, or any other livecd that contains gparted) and shrink the Ubuntu partition and then with the extra freespace resize whatever partition you want to increase (Windows or another *nix distrobution)

Look here for more info: [http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

