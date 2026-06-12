---
title: "In the middle of OS running well, need move /opt directory into a partition"
date: 2020-01-25
forum: Installation &amp; Upgrades
---

### Post by abdulbadii on 2020-01-25
How do we, after now-running OS being installed well, move and separate /opt directory into an exclusive partition /dev/sda.. recognized by system?
I tried to do it on gparted but it create a partition with the status is primary partition instead of /dev/sda... as attributed to the other installation partitions, so I immediately canceled, exited out of gparted as I feel doubt it won't be recognized as supposed to be correctly as its functionality.
How to solve this?

---

### Post by CatKiller on 2020-01-25
[Here's](https://help.ubuntu.com/community/Partitioning/Home/Moving) one guide for moving an existing directory to a new partition. It's set up for /home, since that's the most common one that people would want to do, but you can adapt it for /opt easily enough. There are plenty of similar guides.

The /dev/sd... indicators are simply one way that the system *describes* the hardware attached to it. You're quite likely to have a different drive and partition layout to whatever guide you're looking at, so you shouldn't expect the names and numbers to match. It's unclear if that's where your confusion was. Those names aren't strictly fixed, and aren't super useful. For actual usage you only care about the mount point, and for things like fstab you'd use UUIDs or labels instead.

---

