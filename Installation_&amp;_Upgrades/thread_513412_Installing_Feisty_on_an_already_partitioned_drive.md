---
title: "Installing Feisty on an already partitioned drive"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by Shay Andrews on 2007-07-30
A computer-savvy friend of mine partitioned my hard drive (25GB Windows, 35GB currently empty), but due to family obligations, can't help me complete the install. How do I finish it?

---

### Post by merlinus on 2007-07-30
Boot from the ubuntu live cd, then select the Install icon at the top left of the desktop.

When you get to the partitioning menu, select the unused space.

You will need to create a partition for / (root) and /swap, and if you like, one for /home.

/swap need not be more than 1.5G, and you can split the rest between / and /home.

-merlin

---

### Post by Pumalite on 2007-07-30
Post specs. Memory? Graphics? What are you trying to install: Live Ubuntu or Alternate Ubuntu or Alternate Xubuntu? How many drives? Which partition are you trying to install to? Where do you want Grub ( MBR or partition)?

---

### Post by davidjmayo on 2007-07-30
here's a guide if you need one

guide [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Ryoushi19 on 2007-07-30
Step 1:  Remove windows logo as icon.
Step 2:  Select the ext2 or ext3 partition and set it's mount point as "/"
Step 3:  Click "next"
Step 4:  PROFIT!!! Just kidding.  Success though.

---

