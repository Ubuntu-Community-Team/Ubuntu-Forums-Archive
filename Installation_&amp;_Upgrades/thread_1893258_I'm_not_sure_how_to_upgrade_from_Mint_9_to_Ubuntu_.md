---
title: "I'm not sure how to upgrade from Mint 9 to Ubuntu 11.10"
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by TheoJava on 2011-12-09
A long while back I installed Linux Mint 9 on an HP Pavilion a6120n desktop PC, and now I'm in the process of installing Ubuntu 11.10. I'm not sure how I should go about it though. There are two main things complicating it slightly:

1. I'd like to keep all the user data, if possible.

2. Back when I installed Mint 9, I did so by creating a number of partitions alongside my Windows install, and no longer remember why, or which ones are what. These are the partitions from the left on that bar to right:

 - sda1: NTFS partition, likely the main Windows (Vista) install.
 - sda5: 3.1 gb, swap space.
 - sda6: 15 gb, ext4 partition.
 - sda3 and sda7: Not sure what order they're in. Both ext4. sda3 is 99.6 mb, and sda7 is 109.7 gb (I'm assuming sda7 is the user partition?).
 - sda2: Another NTFS partition, 9.5 gb.

So is anyone here familiar enough with common partitioning practices to feel they know what each partition is supposed to be? I did follow some 3rd party guide to make the install.

How should I go about installing 11.10? Should I delete all the ext4 partitions except the one that I think is probably the user partition?

---

### Post by searchfgold6789 on 2011-12-09
We can't determine what te partitions are likely used for just by their sizes. Could you post the contents of the partitions? (maybe a few folder names?)
Thanks,
 - search

---

### Post by tartalo on 2011-12-09
```
df -h
```

---

### Post by kio_http on 2011-12-09
You probably don't have a user partition. Maybe system and home folder are in the same partition. If so just backup and do a fresh install of Ubuntu. When installing chose manual mode and format sda7 and set its mountpoint to "/"

---

