---
title: "RAID10 on Ubuntu 10.04"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by OMGthatsCrAZy on 2011-04-09
Hi guys,

I just built a NAS machine with 1x 500gb WD blue drive and 4x 2TB WD green drives.

I installed 10.04 on the 500gb drive, and now I am trying to make a RAID10 with the remaining 4 drives, and I keep running into problems.

I tried to use the onboard raid controller (intel 82801) to make the RAID10 and it does but then when I boot into Ubuntu, I see all 4x2TB drives as well as what looks like 2xRAID0 drives.  When I try to use the Disk Utility to make a Raid volume, it fails.  When I turn off RAID in the BIOS and change it back to IDE, I still cant make a RAID volume in Disk Utility after I boot, the drives cant be selected and theyre greyed out.

Does anyone have any experience with this?  Please advise.

-OMG

---

