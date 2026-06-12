---
title: "Encrypted partition mistake"
date: 2014-03-18
forum: Installation &amp; Upgrades
---

### Post by terranz on 2014-03-18
I did something stupid.

I was installing Ubuntu 13.10 on my external HDD to use at work and I had screwed it up so badly before, playing with previous versions, that I thought what the hell I'll let Ubuntu take over the drive while installing and what I got was two tiny /boot partitions and a 900GB+ encrypted partition and no SWAP partition.

Is there any easy way to shrink that partition so I can add a SWAP and something windows can see?

---

### Post by ajgreeny on 2014-03-18
I think you might find it easiest to start again from scratch.

Choose "Something Else" at the partitioning stage and set up the partitions and filesystems that you want.
If you need to share a partition with windows it can either be done with samba, or if you are using both OSs on the one machine, just make a shared NTFS partition, which can be read and written to by both OSs.

---

