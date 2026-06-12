---
title: "Ubuntu on NILFS partition?"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by ansabhailte on 2010-04-22
Hey there all,

First off, let me say that I understand that NILFS(2) is still relatively experimental, so I understand the risks of what I'm asking. Ok, so, I want to have Ubuntu on an NILFS2 partition, meaning that instead of like ext3 or reiserfs I want to install it on NILFS as the root partition. Gparted currently doesn't support it at all, but the nilfs-tools is available in lucid now. I was thinking either to format a partition to nilfs and copy all the files over or something, or even install ubuntu on ext2 then convert the partition to nilfs, but I'm not sure. Any ideas?

---

### Post by jimcooncat on 2010-06-06
I'm just starting to look at NILFS for my /home partition.

I can see that there would be value in using NILFS as a root partition. In particular, /etc would have the huge advantage of multiple checkpoints, and you could save states by creating snapshots. It's not that useful by itself, though, as NILFS now does not have a rollback feature. So you would have to periodically copy your snapshots to a seperate file system.

Anyway, I'd go about installing Ubuntu (or Debian) on top of NILFS by partitioning the hard drive using a live cd like Ultimate Bood CD ([http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)). Boot the live CD, and use the hard disk diagnostic tools to make sure the medium is as sound as you can determine.

You can then reboot with an Ubuntu Live CD. If the nilfs tools are not included, you should be able to install them while in the live cd environment. Then fire up gparted and make an empty partition for your root, perhaps 10 GB (nilfs is not resizable, so pick a good number to start with). While you're in there, make sure you have a swap partition to use, and consider separate /home and /tmp partitions too. Then run the mkfs tool from nilfs on the empty partition to format your new root. Make sure to make note of all the device names you create.

You should then be able to run the Ubuntu installer, taking care of what gets installed to what partition.

Disclaimer: I haven't tried this myself.

---

