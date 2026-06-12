---
title: "Partitioning Question"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by wardog21 on 2007-02-01
Ok i am completely new to linux but i would like to try it out and heres my situatiion

i have 2 hard drives, 250gb with xp and all my games, 80gb with vista. Now i want to partition the 80gb in half for ubuntu. Does ubuntu have built in partitioning? If not, what free program could i use? And i have also heard people talk about a swap file or something like that, saying i need to make a small partition for that?

Any help would be great, thanks!

---

### Post by Ryzol on 2007-02-01
Yes the ubuntu install CD does include its own partitioning tool. 

Swap is basically extra virtual memory incase it needs more than what the RAM provides. I believe you can make a swap of up to 3x of your RAM. However, a 3gb swap when you have 1gb of RAM seems excessive. If you have a system with not much memory (256mb or less) I would go with the maximium swap size. If you have a decent amount of memory (512mb or more) I would go with 1gb to .5gb of swap.

---

### Post by housam on 2007-02-01
> **wardog21 said:**
> Ok i am completely new to linux but i would like to try it out and heres my situatiion

i have 2 hard drives, 250gb with xp and all my games, 80gb with vista. Now i want to partition the 80gb in half for ubuntu. Does ubuntu have built in partitioning? If not, what free program could i use? And i have also heard people talk about a swap file or something like that, saying i need to make a small partition for that?

Any help would be great, thanks!

Yes ubuntu has the Gparted tool for partitioning either before install or during the install. Also you have to create 2 new partitions for ubuntu : one  ( / ) ext3 for the root and one swap format for the swap partition ( 1Gb ).

Also you can download and burn the latest version of Gparted to have a live cd.

---

### Post by Sef on 2007-02-01
> Also you can download and burn the latest version of Gparted to have a live cd.

[GParted]("http://gparted.sourceforge.net")'s site.

---

### Post by AmandaKerik on 2007-02-01
Yes, Ubuntu's setup / installer has a partitioner - it works great imo.

Read a few Ubuntu / xp dual boot installation tutorials, first though.

---

