---
title: "need to uninstall ubuntu/grub (not what it seems)"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by youdidntseenothing on 2008-09-19
Hey there, 
I tried out ubuntu and i must say im a fan now. Right now its on one hdd with two partitions, one with windows xp and the other with ubuntu. However, i'm going to get a new small computer and put ubuntu in there so i want to get rid of ubuntu in this computer. How do i exactly do this. Do i just format that ubuntu partition? and when i do that, whats all this with grub and it being in the mbr?
Thanks heaps

---

### Post by oilchangeguy on 2008-09-19
> **youdidntseenothing said:**
> Hey there, 
I tried out ubuntu and i must say im a fan now. Right now its on one hdd with two partitions, one with windows xp and the other with ubuntu. However, i'm going to get a new small computer and put ubuntu in there so i want to get rid of ubuntu in this computer. How do i exactly do this. Do i just format that ubuntu partition? and when i do that, whats all this with grub and it being in the mbr?
Thanks heaps

there are probably hundreds of threads on the same subject. if you'll simply type uninstall ubuntu to the search bar at the upper right of this page, you'll find many of them. that way the same question doesn't get asked over, and over, and over, and over.........

---

### Post by Herman on 2008-09-19
:) Hello back to you!

You are correct, basically you just need to write some code in the MBR to overwrite the code GRUB put in there to make it point to GRUB in Ubuntu. 
You need to put the code back in the MBR to make it point to Windows's boot sector again.
There are lots of different ways you can do that, and a collection of them are listed and explained here in the following link, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm").
Just take a look and choose a method that suits you.

Then you just delete the Ubuntu partition(s) with a partition editor, such as Gnome Partition Editor in the Ubuntu live cd and resize your Windows to occupy the entire hard disk.

Regards, Herman  :)

---

