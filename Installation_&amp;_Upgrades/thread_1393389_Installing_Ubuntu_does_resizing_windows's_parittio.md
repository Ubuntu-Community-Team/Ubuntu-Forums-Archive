---
title: "Installing Ubuntu: does resizing windows's parittion moves the blocks at the end?"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2010-01-29
There is this thing I am wondering. I have a PC where I want to install a dual boot Win XP + Ubuntu. So prior to doing anything, I am defraging the XP partition. But, there are these blocks that keep staying at the very end of the partition.  If I resize that Windows partition with Gparted on the live CD, will it move or whipe out those blocks (or any blocks) in the partition area that is about to be loss due to being resizing ?

If it whipes them out then a lot of people will have windows problems.

---

### Post by darkod on 2010-01-29
Gparted moves any data that is positioned in the part that will be "cut off" during the shrink. That is a great bonus compared to windows disk management for example, which has option to resize partitions in vista and 7, but only until it hits data.

---

