---
title: "Trying to resize EXT4 partition with MiniTool"
date: 2020-02-17
forum: Installation &amp; Upgrades
---

### Post by rva1945 on 2020-02-17
Hi:

I can resize Win 7 partition but MiniTool only lets me move EXT4 partition between two unallocated partitions. Currently there is a 230GB unallocated partition before EXT4 and a 0GB unallocated partition after. The UP and DOWN arrows to chabge the size don't work.

Do I have to move EXT4 to remain before the unallocated partition so to enlarge it later?

Thanks

---

### Post by CelticWarrior on 2020-02-17
Yes, you have to move it left. But if dealing with EXT4 partitions do it preferably with GParted in a live session.
Most reputable tools for Windows should do it fine but some can corrupt data.

---

### Post by ubfan1 on 2020-02-17
Also, be aware that not all partitioning tools will resize the filesystem when you change the partition size. -- gparted does if the resize2fs program exists.

---

