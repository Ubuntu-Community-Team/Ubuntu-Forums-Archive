---
title: "Installation and partitions"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by chrisbird on 2008-03-23
I'm trying to install Ubuntu 6.10 (from Hagen's 'Ubuntu Linux Bible'.

My 30Gb disk is already partioned as follows: 20Gb for Windows XP, and 10Gb that has never been used for anything and is definitely not formatted as a Windows partition. When I try to install Ubuntu, using 'Use the largest continuous free space' (assuming that will then make it find and use the 10Gb partition), I constantly get returned to the same screen that asks me how I want to partition the disc - it seems to be making an assumption that the 10Gb partition is not there. If I give up on 'Use the largest continuos free space', and opt for 'Manually edit partition table, I see the two partitions: one of 20Gb for Windows and one of 10Gb 'unallocated'. If I then select the 'unallocated' partition of 10Gb for the Linux partition, all that happens is Ubuntu wants to repartition the Windows 20Gb partition.

In other words, and apologies for the length of the above, Ubuntu is failing to see the non-Windows 10Gb partition. Solution anyone, please?

---

### Post by jken146 on 2008-03-23
Hmmm.  It's been as while since I did an Edgy install.  I strongly recommend you get Gutsy (7.10) if you're new to Ubuntu; it is much more up to date.

---

### Post by chrisbird on 2008-03-23
Good advice ... but dare I mention bandwidth and dialup speeds? :-(

Afraid I'm stuck with 6.10 until a 7.10 disc arrives in the indeterminate future.

---

### Post by jken146 on 2008-03-23
Alright then, Edgy it is.  You need to do more in the manual partitioning page than just select the empty space.  You have to create some partitions and specify their file system types and mount points.  You'll need an ext3 partition for / and a swap partition for swap (swap should be ~ RAM x 1.5 but not more than 1 GB in size).

---

### Post by chrisbird on 2008-03-23
Ah, but that's where the dilemma starts. 

When I do select the 'unallocated' partition of 10Gb for the Linux partition, and try to create partitions as you suggest, all that happens is Ubuntu reverts to wanting to partition the Windows 20Gb partition. It ignores the fact that I've selected the unallocated 10Gb partition and that I'm trying to get it to partition that.

---

### Post by wglastonio on 2008-03-23
Hi all,
I have the same problem. I created a new partition before installation using Gparted but during the instalation Ubuntu doesn't recognize its. The Ubuntu installer only shows one option to install using entire disk.
Reg,
Wg.

---

### Post by chrisbird on 2008-03-23
I've sorted it, and need my proverbial a*** kicking. 

Although I selected the 'unallocated' space of 10Gb for the Linux partition, and then moaned that Ubuntu wanted to repartition the Windows 20Gb partition, it totally passed me by that I also needed to click 'New' to create a partition it could understand, rather than just assume it would would happen automatically.

Tut, tut :-(

However, I appreciated your speedy responses, jken

Regards, Chris

---

