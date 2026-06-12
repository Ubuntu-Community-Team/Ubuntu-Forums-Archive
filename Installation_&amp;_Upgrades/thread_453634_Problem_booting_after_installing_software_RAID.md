---
title: "Problem booting after installing software RAID"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by Kazol on 2007-05-24
I [finally] managed to install software RAID-1 in Feisty on 2x10GB HD, the root fs on md0 and swap on md1. I verified that RAID was working-it displayed everything as active. I finally tested it out by removing sdb (the second HD) and changing the jumper to single on the first (the BIOS does not recognize that the drive is even there-would setting both HDs to CS help?). It only booted until the ubuntu logo, where it froze with the error msg "waiting for root filesystem."
I don't understand how it cannot find the root fs (which is on the disk itself).

---

