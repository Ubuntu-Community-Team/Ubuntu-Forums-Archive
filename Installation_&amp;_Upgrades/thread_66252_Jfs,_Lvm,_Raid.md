---
title: "Jfs, Lvm, Raid"
date: 2005-09-16
forum: Installation &amp; Upgrades
---

### Post by yamla on 2005-09-16
Intro:  I have a fair amount of Linux experience, including submitting a patch to the kernel folk in the past.  I've been using Ubuntu for a while.

I'm about to build two Ubuntu systems over the weekend.  I have both Hoary Hedgehog and Breezy Badger installation CDs but I think I'm better off sticking with Hedgehog for now, right?

Anyway, for one the machines, I want to use JFS for my /home partition.  IDEALLY, I'd like to stick that under LVM.  Is this suicidal?  My / partition would be ext3 or reiserfs and I could go with a /boot partition as well if that helps, though I can't imagine how it would here.

The other machine has four 300 gig SATA hard drives hooked up to a software-RAID5 (sil3114) controller (obviously, this is 'driver supported' at best, not real RAID-5).  I'd like to use Linux software RAID-5 on these, ideally both for / and for /home.  Will this even work in Hoary?  In Breezy?  At all?  Reiserfs and/or ext3 in this case.  Is LVM a possibility for /?

Would it help if I added a PATA drive and stuck root on there?

Any horror stories of JFS and reason to prefer XFS?

---

