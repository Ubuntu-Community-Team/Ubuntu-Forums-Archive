---
title: "Noob Dual Boot Install"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by Calculus on 2006-09-28
Cheers all,

I'm looking to install and use Ubuntu/Linux under dual boot conditions for the first time on a new notebook.  The 60g hd came partitioned into two roughly equal FAT32 partitions.  I would like to get some opinions on how I should handle any repartitioning on the hd.  

Searching around I came across the following scheme. Shrink the windows partition to as small as possible, install Ubuntu in its own small partition, leave the swap at the end of the drive, and make the remaining space a /home - shared data Ext3 partition.

According to the author I can use a program called FS-Drive which allows Windows to read and write to Ext3 partitions.

I'd like to know if this is a good idea, what people think of FS-Drive (does it work well?), and if anyone has a better solution.

Thanks

---

### Post by tombiz on 2006-09-28
Here are some resources that I found to be helpful:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/)

---

### Post by Calculus on 2006-09-28
Thanks for the links, I'll check them out.  Anyone else have any thoughts?

---

