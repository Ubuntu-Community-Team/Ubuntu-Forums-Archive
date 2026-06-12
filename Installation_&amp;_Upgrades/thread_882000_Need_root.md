---
title: "Need root"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by jhmac77 on 2008-08-06
I tried to install 8.04 but it always wanted to install the whole disk with Ubuntu, **DESTROYING ALL MY OTHER DATA**.

I need the root to install manual. For a person who really knows explain in detail.  Please!!

---

### Post by tuxxy on 2008-08-06
You need to make a partition on your harddrive for ubuntu, have you read the installation guide

[https://help.ubuntu.com/8.04/switching/installing.html](https://help.ubuntu.com/8.04/switching/installing.html)

---

### Post by oldos2er on 2008-08-06
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

---

### Post by jhmac77 on 2008-08-07
**I have done that** but **Ubuntu won't write over that partition**.  What does that have to do with "root".  If you go to manual install, it always asks for the "root".  Why does it ask for the "root" if I can't come up with the root?  

Maybe someone that is more expert can answer this question.  I am not getting an answer to my question.  I can make more partitions, yet it says under one instance of my install menu that I may have too many partitions, which I doubt very much.

Nobody seems to know the answer.

---

### Post by jhmac77 on 2008-08-07
What is the Quick reply icon?  not clear.  As to the above situation, when I try to install in the free space, it says I may have too many partitions.  Is 1 too many partitions? or 2?

---

### Post by Partyboi2 on 2008-08-07
You can only have 4 primary partitions, so make a extended partition then create under the extended partition the partitions that you need to install ubuntu. Make sure when you select the / (root) partition that you set the mount point as / other wise it will complain that no root mount point has been set.

---

### Post by louieb on 2008-08-07
When installing -  root (/) is the partition you want to install Ubuntu in.  It asking for root because the installer want to know where.

If you have already made a partition to install Ubuntu in. Use manual partitioning. Select the partition, choose edit, select mount point and select / (root).    

If you have more questions I will need see the partition table. to do that.
open Applications>Accessories>Terminal and run 
```
sudo fdisk -l 
```(lowercase L)
Copy the output in your next post.

---

