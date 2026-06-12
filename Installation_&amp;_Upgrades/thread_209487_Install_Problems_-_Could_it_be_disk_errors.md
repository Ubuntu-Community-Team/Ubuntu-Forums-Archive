---
title: "Install Problems - Could it be disk errors?"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by richardq on 2006-07-05
I've tried several different ways of installing Dapper and I'm beginning to think I'm dealing with a disk problem rather than a software problem. I've got a pc with 2 internal hard drives. Each one has an ntfs partition on it with XP-home and I'm attempting to install Ubuntu into the remaining spaces. Here's what I've done:

1. installed from the Dapper-desktop iso -> using install icon from desktop, the installation appears to complete fully but Grub just hangs when I try to restart. (the desktop-iso install doesn't ever ask me where I want to install grub so I'm not sure if the actual install is completing properly or not)

2. installed from Dapper-alternate iso -> installation fails (or display at least fails) right after it configures xserver-xorg. the base system installs, but the display goes black with a couple of white rectangles during the next step.

3. installed from my old Breezy install CD -> this worked fine last year, but this time around it stopped during the base system install at some point involving init.rd and won't let me continue.

Because each install method fails at different points (and I've tried each of the three at least two times), is it possible that I'm dealing with some disk errors? Each time I ask the partitioner to format all the new partitions so I thought this would eliminate any disk errors (bad sectors etc..). Is there some other way to check the empty spaces on the disks so that the bad sectors get marked as such prior to running the installation?

I'm thinking of moving both my XP partitions to the same drive, thus leaving a complete hard drive (the slave drive) to install Dapper on. Is this a better idea? That way I could format the slave drive completely prior to installing Dapper.

---

