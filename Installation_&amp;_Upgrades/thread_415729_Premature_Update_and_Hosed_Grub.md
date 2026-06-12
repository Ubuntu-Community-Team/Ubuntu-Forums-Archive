---
title: "Premature Update and Hosed Grub"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by fineghal on 2007-04-20
So I did a dist-update dist-upgrade the other day and it completely hosed my grub menu. 

Everything is still there, just pointing to the wrong places.
(Well the linux stuff is. The windows one works fine)

Setup as follows:
These are sata drives btw.

sda - windows

sdb - Partition E: (Prime)
         Partition AF (Prime)
         Extended Partition Containing another Partition and Swap
         Partition (Prime) which is the / partition.

The grub menu gives cannot mount errors with all the linux stuff.
I check the commands and they all say hd(1,2)

Suspecting this is my problem, I change to hd(1,3) and memtest boots. So obviously that part is right (and /boot still exists.)

I try this with my other grub entries. Linux 2.6.17 for example, and it starts to load, and then gets a "Waiting for root device." And eventually drops me into the ash shell.

I don't have the grub window open right now, but it was working pre update/upgrade. The only drive "flag" I can see is where to set the root device. Right now the root device is = /dev/sdb3.

Is this correct? I've tried fiddling with it but no luck. 

Solutions? I've done a LOT of customizing on this and do NOT want to reinstall. 

So ways to:
A) Fix the grub line(s).
B) Can I mount the system to ram? I've got 3-3.5 gigs, and that seems like it should be possible. I could even GUI it... Running fluxbox.
C) Tips to use a livecd to recover things or salvage and then reinstall? 

Thanks!

Oh and ps: Running 965 board with irqpoll as a boot option. Pesky jmicron controller. :roll:

---

