---
title: "Just installed Ubuntu -- but I can't see windows on GRUB"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by MrMatt2532 on 2007-04-29
I have 3 partitions (1 hd), 2 for ubuntu and 1 for windows xp, and they are grouped as shown:
/dev/sda1
     /dev/sda5 -- windows
     /dev/sda6 -- swap partition
/dev/sda2 -- ubuntu

I don't know why they are grouped like this, but after i installed ubuntu, windows xp didn't show up on the grub boot loader.

I tried:

title Windows
root (hd0,0)                            <--also with (hd0,5)
makeactive
chainloader +1 

and 

title Windows
rootnoverify	(hd0,0)             <--also with (hd0,5)
savedefault
makeactive
chainloader	+1

both with no success. Can someone help me out here? Thanks.

---

### Post by bulldog on 2007-04-29
> **MrMatt2532 said:**
> I have 3 partitions (1 hd), 2 for ubuntu and 1 for windows xp, and they are grouped as shown:
/dev/sda1
     /dev/sda5 -- windows
     /dev/sda6 -- swap partition
/dev/sda2 -- ubuntu

I don't know why they are grouped like this, but after i installed ubuntu, windows xp didn't show up on the grub boot loader.

I tried:

title Windows
root (hd0,0)                            <--also with (hd0,5)<--make this (hd0,4)!!!!!
makeactive
chainloader +1 

and 

title Windows
rootnoverify	(hd0,0)             <--also with (hd0,5)
savedefault
makeactive
chainloader	+1

both with no success. Can someone help me out here? Thanks.

I have posted something in your post above have a look and try it.

But FYI,it's best to have windows on the first primary partition!!
If you've managed to get windows in a logical partition,I'm afraid you won't get it to boot.
But I'm not sure if you did that,can you give me info about sda1?

You van copy your data if you want by mounting your partitions with the live cd,and copy your data to another disk.

---

