---
title: "Create shared data partition for all users with read write permisson"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by amitsgokhale on 2008-09-28
Hi,
I just installed the Ubuntu 8.04 on my system. I partitioned my 120 GB HDD with following specifications.

20GB '/'
20GB /home
2GB  /swap

remaining space is unallocated (around 60GB). Now I want to create a partition to store all my music and movies and other stuff so it can be accessible to other users who use the computer. Also that partition should get auto mounted on every boot and have read and write permission so other people in home can also store photos and music.
I don't want to share my home folder to other users.
Can anybody tell me how to make this new partition?

---

### Post by olejorgen on 2008-09-29
1. Install gparted and make a partiton.
2. Make a mount point with rw permission for everyone (if you use ext2/3 at least)
3. Add the partition to fstab
4. sudo mount -a

---

