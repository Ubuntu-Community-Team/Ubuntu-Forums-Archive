---
title: "Kubuntu Feisty Raid0 install problem(s)"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by D4mn on 2007-07-31
Hi there.

I have two WD disks that I want to use in a stripe-set and want to instal both Windows and Kubuntu7.04 on my raid0 array. I have a Gigabyte GA-965P-DS3 mainboard, with Conroe 6600.

I understand that the /boot partition cannot be installed on a stripe-set, so I will have to put this on a separate disk / array. Also I need the Kubuntu Alternate CD to make raid work at all.

1:	Does anyone know whether I can make multiple array's on my disks (to make 1 mirror array and a stripe-set on the 2 discs) ? 

2:	I have one other really awkward thing. When I create the array and install WindowsXP, things work okay. When I boot the Fiesty LiveCD (the normal one) somehow something is written to one of the discs and the stripe-set is broken :( had it three times now. Any experiences ?

3:	Do I need to enable AHCI for RAID to work correctly ?? What if I turn it off ??

4:	Can grub install when XP is installed on the first partition and NTFS is used ??

A lot of questions, hope somebody can help me with this.

Thanx.

D4mN..

---

### Post by Pumalite on 2007-07-31
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by D4mn on 2007-08-03
Mmm. somehow my Gigabyte Raid controller sometimes remembers (??!??!) an old array, causing it to fail... I gave up installing my whole OS on the raid0, getting it to work as data disk is the next step, but undoable with this failing controller. 

Anybody got experience with this ??

The rest was made clear through the link that was sent to me...

---

### Post by dabl on 2007-08-03
Your motherboard hardware RAID controller isn't the way to do it in Linux.  I haven't tried to set up a RAID in Linux, but what I read indicates there are basically 2 approaches to it.  One uses something called mdadm -- you can search on that.  The other uses dmraid like so:

[http://www.linuxquestions.org/questions/showthread.php?t=567935](http://www.linuxquestions.org/questions/showthread.php?t=567935)

:)

---

### Post by D4mn on 2007-08-06
Thanks. I figured that one of the two indeed would work for me. 

But I still have the weird problem of my controller remembering stuff... Also when I create a mirror, I also get messages my disks are being degraded for no particular reason...

Anyway, I have my old (actually the same) disks for my OS and can mess around with my raid controller. I am thinking of buying a HW raid controller though...

Thanks !

---

