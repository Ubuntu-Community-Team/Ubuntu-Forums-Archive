---
title: "RAID 0 and GA-965P-DS3"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by Vipersfate on 2009-12-06
I've been trying to install 9.10 on a RAID 0 array. I'm not quite sure how to get going with it.

My motherboard BIOS is set properly (I've used RAID for Windows many times), and the install will not see the drives. The live CD sees the drives, but as separate drives, rather than a raided array.

I have 2 80GB WD in a RAID 0 with 128kb stripe size. Does anyone know how to get going with this. Thanks!

---

### Post by Vipersfate on 2009-12-06
Well, I figured it out. It was that the normal live CD did not come with MDADM I think it was called. Installed it, and raid works!

Ubuntu installed to the raid, but on reboot, my Gigabyte raid alerts me that the disk are no longer raided. I'm at a loss now. No clue what to do.

---

### Post by Vipersfate on 2009-12-07
Bumpages.

---

