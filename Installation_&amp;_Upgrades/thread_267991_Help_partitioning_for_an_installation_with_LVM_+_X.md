---
title: "Help partitioning for an installation with LVM + Xen"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by cheuschober on 2006-09-29
Hi-

First and foremost. I'm totally new to the idea of LVM but I'd really like to learn. Please understand that when replying. Now, continuing, I'm converting my htpc over to an ubuntu based mythbox and need suggestions partitioning.

First off, relevant specs:
AMD AM2 X2 (64-bit, SMP, VT)
HDD0 - 36GB WD-Raptor
HDD1 - 160GB Samsung
HDD2 - 160GB Samsung

Okay, so here's where I get muddy - In the nearish future I'll need to install Xen and get an installation of XP on the box (solely for foobar2000, can't live without that program for album management and there isn't anything even close in linux... yet). I've been reading what I can and I don't think I could handle Xen yet but I think I have at least the basic understanding that Xen does not need its own partitions but most people working with Xen have been using LVM for some reason or another and I'm just spinning in circles wondering what / how to use this LVM.

The 36GB raptor is my host drive. Obviously my /boot partition will go here. After that I'm also planning on having / and /home as separate partitions (volumes? not sure on the right terminology here).

On the 160GB drives I want to have several partitions/volumes striped. One should be /tmp, one should be devoted to a myth backend, and one given over to xp. Unfortunately I don't know how much space I'd need for /tmp or XP for that matter.

As to file systems:
/boot - ext2
/ - ext3
/home - ext3
/tmp - xfs
?/myth - xfs
?/xp - fat32


I understand from something I read that LVM can stripe but the performance enhancement equivalent with the linux software raid striping?

Again, assume I'm a total newbie to lvm and am completely ignorant of pv's and lv's and such -- how would you recommend I set up this machine?

---

