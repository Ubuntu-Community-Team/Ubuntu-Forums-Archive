---
title: "RAID and LVM issues"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by Arricc on 2007-06-16
Hey folks,

I'm having no end of problems with the alternative installer for Feisty.

My ultimate goal is to have 2 drives with LVM running on top of a software RAID1.

For some reason, it just doesn't work.

I seem to be unable to create logical volumes on top of volume groups - the processes just seem to hang. If I kill it then the installer moans at me, but lvdisplay seems to think that they're created ok - but I can't setup the logical volumes as actual partitions - even when I force the installer to autodetect the partitions again.

I tried setting up the partitions by hand just on top of the RAID, without and LVM, and had a similar problem - I appear to be able to create a max. of 1 partition!!!

Additionally I tried abandoning the RAID and going for a RAID0 equivalent volume group with my drives in 1 big pool, but still was unable to setup any logical volumes as partitions!


I've done this type of setup before with Debian Sarge and had no problems!

Is the installer just fundamentally broken???

Cheers.

---

### Post by raijinsetsu on 2007-06-16
There's a problem with the LVM on the alt-install disk. If you leave it (I had to leave mine for 5-10 minutes for each LV creation), then it will work. It's a bug, and it sucks. Something to do with a device timeout problem.

---

