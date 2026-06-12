---
title: "linux installer cannot see raid configurations"
date: 2012-12-12
forum: Installation &amp; Upgrades
---

### Post by cwrubiophysicslab on 2012-12-12
Hello all,
I am assembling a new computer with an asrock z75 pro3 motherboard, and I would like to set my machine up with a dual boot for both windows 7 and linux. I originally set up a pair of SS harddrives and 3 spinning disk drives in two separate raid 0 configurations in the motherboard bios. I installed windows on the SS harddrives and set a region up on the spinning disk drives for linux, but when I tried to install linux it did not see the partition. I have tried both 12.10 and 12.04 and wubi, they all have the same problem.
However, if I go back and delete the spinning disk raid volume, it now sees the three separate drives and says there are no other operating systems on the machine.
I could just install linux on one of the hard drives, but I am not sure if dual boot will still work properly and I would really prefer to have the raid 0 configuration available to both operating systems.
Looking briefly over some of the replies, it seems some people are suggesting updating drivers, but I don't see how this can help when I am installing linux from scratch.
Can anyone help?
Thank you in advance!

---

### Post by arpanaut on 2012-12-13
If You use the Alternate iso for 12.04 it should work.
For 12.10 there was a big change in the installer, as they were trying to eliminate the alt. iso version, but were not able to get the raid part of the install into the release-- time constraint.
It is planned for all installation options to be included with the 13.04 installer.

I personally don't have experience installing linux on raid, but the standard advice is to use the alternate iso to get it done.

Dated but should be good guide. [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

HTH

---

### Post by cwrubiophysicslab on 2012-12-16
Thanks!

---

