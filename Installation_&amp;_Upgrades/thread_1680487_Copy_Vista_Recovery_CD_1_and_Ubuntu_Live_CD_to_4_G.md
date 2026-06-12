---
title: "Copy Vista Recovery CD 1 and Ubuntu Live CD to 4 GB Flash drive?"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by carlos123 on 2011-02-02
I have been experiencing a fair bit of problems trying to get my computer to dual boot between Ubuntu 10.10 and Vista.  If I restore the GRUB it messes up Vista booting (i.e. it won't boot up, neither will it boot into the recovery partition).  If I restore the Vista boot sequence (which overwrites the MBR again) it obviously messes up the ability to use GRUB to boot into the Linux partition. 

Anyway...until I figure out how to fix that...I would like to put both the Vista Recovery CD 1 AND the Ubuntu Live CD on to one flash drive instead of having to carry around the two seperate CD's.  

There should be a way to do this.  

I was thinking...

- Create two partitions on the USB. 
- Copy the contents of Vista Recovery CD 1 to one partition
- Copy the contents of Ubuntu CD to other partition
- install GRUB on the USB flash drive manually on one of the partitions.

The parts I don't know how to do is copy the contents of a CD to a particular partition (I can copy the contents to an entire device using dd but don't know how to copy to a partition among many). 

And install grub manually (sudo grub-install --root-directory=/dev/usb???)?

Any advice or input on this would be most appreciated. 

Thanks. 

Carlos

PS.  By carrying around the USB (assuming I can set this up) I will be able to boot up to either the Vista Recovery CD or the Ubuntu Live CD.

---

