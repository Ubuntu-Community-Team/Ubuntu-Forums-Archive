---
title: "Ubuntu Studio Partition help!!"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by compelite on 2010-07-01
Hi, I really want to install Ubuntu Studio but I want to be safe while installing it. So here is what I did, I created two partitions, the first partition I created is called "Ubuntu OS" and that is roughly 10 gigabytes. The second partition I created is called "Ubuntu Swap" and that is roughly 10 gigs as well. 

Now, when I start the Ubuntu Studio Installation from the dvd, I get the the part with partitioning and everything and I get confused. How do I make it so I can install it on those two empty partitions that I created? Any help would be immensely appreciated! cheers,

---

### Post by ronparent on 2010-07-01
Opt for a 'manual' partitioning (the third choice). This will bring up a new screen. Just select the partition you have already created to install to and select change. In the resulting pop up, just be sure to select a mount point - /. The format to be used and the format check nark are optional.

---

### Post by compelite on 2010-07-01
I come up with an error saying debootstrap warning, so I have a fat32 partition and a ext3 partition. But I need to make sure I setup the swap partition as well. =S so many partitions.

---

### Post by celldweller1591 on 2010-07-01
Delete both partitions you created , goto partitioner setup and select "manual partitioning" and make one "/" and one "swap" partition, size of swap should be double the size of your RAM. Rest should be root "/" partition size. Select root to be ext3/ext4 and done !

---

