---
title: "HELP:  Cannot boot from secondary drive of software RAID1 array"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by theosib on 2006-09-05
I have two identical 120GB drives, which I have set up as a software RAID1 array.  My objective is to be able to suffer one disk failure and be able to use the other until a replacement arrives.  

As a test, I tried booting with each of the drives disconnected in turn.  When the secondary is disconnected, it boots just fine.  When the primary is disconnected, I am unable to boot from the secondary.  BIOS settings and rearranging cables do not help.

My best guess is that GRUB was not installed on the secondary drive.  I've reported this as a bug ([https://launchpad.net/distros/ubuntu/+bug/58894)](https://launchpad.net/distros/ubuntu/+bug/58894)).

I would like to go ahead and start using this system, but I don't want to as long as my data is at risk.  If the primary drive dies, I have no way of recovering.  What's the point in using RAID1 if loss of the primary disk is fatal?

So, in the short term, I was wondering if someone could help me figure out how to fix the problem.  I know nothing about GRUB (I specifically chose Ubuntu so I wouldn't have to learn these things), but I'm guessing that I just need to install GRUB on the secondary disk in such a way that it will let me boot that drive when it is the only drive.

Can anyone help me, please?

---

