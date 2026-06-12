---
title: "optimal partition sizes"
date: 2005-10-09
forum: Installation &amp; Upgrades
---

### Post by GOwin on 2005-10-09
a few days ago, my hoary installation crashed. i guess i wasn't lucky that day - power loss while shutting down = hosed ubuntu. (windows in the other partition is still working fine though)

it's a laptop dual-booting 20Gb on windows 2000. w2k uses ntfs, i got a fat32 shared drive. i use /home on a separate partition.

after re-installing hoary, i decided to do a dist-upgrade to breezy. i ran out of diskspace!

being new to customizing partition sizes, i'd like to ask how much space should i allocate for root and home partitions? because when i installed hoary, i allocated about 800 mb for root, 2 Gb for home, and allocated spaces for /usr , /etc and /var and /opt.

if i put /usr in a separate partition, does that mean i get to retain my applications in case my system goes down again?

---

### Post by az on 2005-10-09
If you had put everyting on one partition, your system would not have had any problems.

There is no point to putting everything on seperate partitions on a desktop computer.  You need to make sure that none of your partitions will run out of room, and so you are limiting yourself a lot for no real gain. 

You need a minimum of just over two gigs of HD space to install the basic ubuntu system.

---

### Post by GOwin on 2005-10-09
sorry, but i don't agree with that.

had i put my /home in the same partition, i would have lost it by now. :(

---

### Post by aysiu on 2005-10-09
I agree--too many separate partitions is often not necessary. A /home partition, however, is a good idea to have.

---

