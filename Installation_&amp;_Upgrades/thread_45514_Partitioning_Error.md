---
title: "Partitioning Error"
date: 2005-06-30
forum: Installation &amp; Upgrades
---

### Post by port7 on 2005-06-30
Hi,

I am trying to install Ubuntu on a HP Brio. When I run the install it gets to the bit when it starts to create the ext3 filesystem on the partitions and it just stops. I have tried it on 2 different 20GB disks and it stops at 13% and then I tried it on a 40GB disk and it stops at 6%.

This is really strange I have checked the BIOS and there doesn't seem to be anything that could cause this there. I am guestimating 6% of 40GB is approx 2.4GB and that works about the same for 13% of the 20GB disks.

Any idea's people? This is really foxing me...

---

### Post by mingus on 2005-06-30
What is the Brio model?

---

### Post by port7 on 2005-07-01
Sorry its not a Brio, it's a <b>Vectra XE310</b>

---

### Post by mingus on 2005-07-01
Some Brio's have BIOS HDD capacity limitations, but the XE310 (at least the Series 2) can see about the 32GB barrier, so that wouldn't appear to be the problem.  

And the HP hardware guide indicates that the XE310 was tested with Mandrake 8,
so Linux would seem to be OK with it.  But look into HDD kernel arguments, you may e.g., need to turn off dma initially.

I'd use a Knoppix CD and try to partition and format the disk with it; you'll get better error feedback than the Ubuntu installer.  Knoppix is fantastic with hardware detection; look at dmesg after it boots and you may see a disk related error.  If Knoppix also chokes and you can find it, try the 3.4 version.  It uses the 2.4 kernel; there have been changes in 2.6 that upsets some hardware.  This would help you determine if the problem is in the OS vs the hardware.

Hope that helps.

---

