---
title: "My friend's Ubuntu won't install"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by Pilot-Doofy on 2007-04-28
My friend has an HP DV8000 notebook and he can't get the Ubuntu partition manager to work properly. Here is a screenshot of what he sees when he brings up the partition manager.

[http://i14.tinypic.com/2qv5yzp.png](http://i14.tinypic.com/2qv5yzp.png)

That picture is taken in high resolution.

---

### Post by SendDerek on 2007-04-29
I'm not an expert, but I'm pretty sure I've installed a linux system enough times to know a thing or two...

First, where's the ext3 partition?  There's fat32 and ntfs, but no ext3?  Can you install linux on fat32?  I've never tried or thought of trying because ext3 is supposed to be better anyways, so why not?

The second thing I noticed is that there's no partition set aside for swap.  I'm pretty sure this is necissary (correct me if I'm wrong).  

Third thing I noticed is that there isn't a partition for "/" or root.  This will need to be done through the partition editor there on the screen.  I can't remember how to do it though.

I've attached a screenshot of what my partition table looks like in gparted.  Don't pay any attention to that totally blank partition.  That was an accident and I havn't merged it with my home partition yet.  

I hope at least some of this helps you out.

---

### Post by Pilot-Doofy on 2007-04-29
Is there any option I can use to just install it with Windows XP and just set it up automatically? There's only Windows XP on this computer, and I just want Ubuntu and GRUB put on it.

---

### Post by SendDerek on 2007-04-29
A manual edit of the partition table is the only way.

There are a bunch of guides out there that will walk you through it.  I would personally recommend to use a program like partition magic in windows to setup your partitions and then use the live cd to designate which one is which.

Partition magic isn't free though, so you may want to try ranish parition manager.
[http://www.ranish.com/part/](http://www.ranish.com/part/)

They even have a step-by-step guide to dual booting:
[http://www.ranish.com/part/dualboot.pdf](http://www.ranish.com/part/dualboot.pdf)

Don't give up on it... it's really rather easy once you get the partitions setup.  The installation will automatically take care of GRUB for you.

It looks like your friend has the same size HDD as me.  Feel free to use my screenshot as a helper or a guideline to getting yours installed.

Basically, you'll need 3 partitions at least (in this order):

1 - Windows XP - NTFS - 80GB
2 - Swap - SWAP - 1GB
3 - Linux Root "/" - ext3 - 10GB

I hope this helps.

---

