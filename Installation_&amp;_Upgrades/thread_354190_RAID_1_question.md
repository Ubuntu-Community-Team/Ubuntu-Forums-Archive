---
title: "RAID 1 question"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by craiger316 on 2007-02-05
I have a [HighPoint 1520]("http://www.highpoint-tech.com/USA/bios_rr1520.htm") RAID controller and I wish to install Ubuntu to the drives hooked up to that sucker.  I've chosen RAID 1 in the controller's bios giving me a mirrored setup.

The problem is, the card is not supported by Ubuntu out of the box (carps on install), so I will have to compile the driver from the vendor.  

I was wondering, would it be possible to follow this scenario:

1) Remove the RAID card
2) Hook one of the drives directly into the motherboard
3) Install Ubuntu onto this drive
4) Compile and install the RAID driver
5) Re-install the card and hook the newly installed ubuntu drive up as the primary, and the blank drive up as the secondary on the card

Will that cause the RAID card to automagically go "hey, the primary drive has stuff that is not on the secondary, I'll start mirroring the drive"  Or will I have to copy the partition over to the secondary drive manually?

Not sure if this is a general RAID 1 question, or if it would be specific to the card itself.

Any help would be greatly appreciated.

Thanks,

Craig.

---

