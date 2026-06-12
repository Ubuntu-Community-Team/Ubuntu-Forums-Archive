---
title: "Dual Boot XP and Ubuntu-Partition Setup"
date: 2005-03-09
forum: Installation &amp; Upgrades
---

### Post by Martimer on 2005-03-09
I am getting a error in the partition setup that refers to no disk format.  I need to know what a typical setup will be.  

Specs:  20Gb HDD.  
Windows XP already installed.
Created a ext2 partition with Partition Magic 8.0.
I reserved a 4.5 Gb partition for Ubuntu, but in the partition phase it errors out.

Any ideas will be welcomed.

MArtimeR :evil:

---

### Post by wallijonn on 2005-03-09
Did you manually select to partition Ubuntu? Instead of selecting "Use Whole Drive," select manual. Then make it select all unused space. Since you have already set it up for EXT3 you may have to manually delete it and have Ubuntu use the rest of the drive so that it can create a swap area.

---

