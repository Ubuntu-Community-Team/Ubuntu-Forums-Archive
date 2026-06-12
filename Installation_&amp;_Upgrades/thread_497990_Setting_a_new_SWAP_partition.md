---
title: "Setting a new SWAP partition"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by jeroenisblij on 2007-07-10
I have Ubuntu installed on a partition on my sdb disk, and i have a 2gig swap partition on this same disk. But my system is kind of slow at the moment, one of the reasons is the slow harddrives, i'm trying some things to speed it up. Today i had the idea that i can spare some space at my sda disk, and make a swap partition on this disk. Then the swap partition would be on another fysical disk than the operating system, and therefore might speed things up a little. I shrinked my windows partition and created a 2G swap partion on my sda. Some questions:

- will this probably speed up my system? Is it a good idea to have your swap on another disk than your  linux partition, or won't this make much of a difference. 

-how do i set ubuntu to start using this swap partition? Will it automatically detect the 'new' swap partition on the other disk, or do i have to set it manually? Can i just delete the old swap partition?

- is it possible and recommended to keep both swap partitions and use them simulatiously? Kind of like a striping idea?

---

### Post by BobbyBionic on 2007-07-12
Hi

I'm not sure this will solve your slowing problem.

Nevertheless it is a good idea to have another swap partition on another part of your harddrive or on another one, you just have to notice the new one on the fstab and it will work (after reboot). You can use both at the same time (it's recommend sometimes to have one at the beginning and one at the end of a drive).

---

