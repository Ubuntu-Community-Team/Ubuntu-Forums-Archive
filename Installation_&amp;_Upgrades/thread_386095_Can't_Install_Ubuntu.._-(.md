---
title: "Can't Install Ubuntu.. :-("
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by mmilitia9 on 2007-03-16
(Very sorry to repost.. I feel that because the other post has 7 replies that people believe it is solved)

I tried 3 CDs to make sure it wasn't a corrupted CD and downloaded twice.

I resized my partition with GpartEdand gave Ubuntu 13 Gigs and 2 gigs for the swap(?). I couldn't rename them or anything(Like I read where you should name the bigger one / and the other swap(?)). The only option I could do to my newly partitioned stuff was change it into Ext3 
I was expecting Ubuntu to pick up the newly created partitions and everything would be fine, but I soon found out it wasn't happening.. But anyway.. before I get to far ahead of myself..

I put in the CD for Ubuntu. Everything seems to work and load fine. I hit the first option for install or boot and then the Ubuntu logo comes up with a loading bar that goes back n forth. This stays on the screen forever.

What should I do?


(I have a feeling because the partitions have no names Ubuntu doesn't recognize anything? Although, When I've installed Mandrake or Suse.. this was never a problem.  Actually, they had there partitioning program included with the software) 


[B][B]Heres my hardware:

Intel® Pentium® 4 CPU 2.80GHz @ 2799MHz (Intel Corporation D845GVSR mainboard)
(RAM) 1GB
(HDDs) 120 GB
(VGA2) NVIDIA GeForce FX 5500 (OS) Microsoft Windows XP Home Edition (SP2),
[/B][/B]

Thanks,

Dominick

---

### Post by eapache on 2007-03-16
How did you use the partitioner if Ubuntu won't boot?

---

### Post by mmilitia9 on 2007-03-16
I dunno what you mean.  I used gparted to partition it. (GParted is the Gnome Partition Editor application.)

Soo.. Thats how I made my partition.  

[B]
Actually, to be honest.  When I tried to install Ubuntu without doing any of the partition steps.  It still didn't work.  I figured Ubuntu would just let me install over XP or have a partition program installed in the installer like Suse and Mandriva has..[/B]

Dominick

---

### Post by zvacet on 2007-03-16
In one step you have to choose mountpoint and that is it.when you open that you will se mountpoint root / and that id your choice for bigger partition.Exactly same for second(mountpoint swap).

---

### Post by mmilitia9 on 2007-03-16
"Most people today prefer the 'Desktop' Live/Install CD for installing Ubuntu with.
The 'Desktop' CD is generally faster and also easier to use. It features a nice graphical GParted partitioner so you can see what you are doing. "


.... Gparted is in the Ubuntu installation?  so I DONT have to really set up a partition before I try to install the actual OS?

I believe I have a bigger issue then.

HELP!


Dominick

---

### Post by zvacet on 2007-03-17
Rerun installation.At the point when you decide how to partition choose manualy.You will see all your partitions.If partitions you made befofe are still there pick bigger one and sign it as root.Second will be swap.If you see just win partition then make partition of free space.You can make exactly same as you described in your post.

---

