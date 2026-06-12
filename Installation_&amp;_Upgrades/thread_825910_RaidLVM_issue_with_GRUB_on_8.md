---
title: "Raid/LVM issue with GRUB on 8"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by pmilano1 on 2008-06-11
Greetings all-

  I'm setting up a box with v8. 

  I have two controllers with 8 disks each, setup as a HW Raid 1+0.

  My OS looks like this:

  /boot (512MB SW RAID1 - EXT2)
  swap  (32GB SW RAID1 - swap)
  /     (1.1TB+ LVM span - EXT3)

  Everything that can be bootable is bootable. 

  I install Grub on the MBR, and it fails with an error 17. 

  The partitioning isn't a problem right?

Thanks-

P

---

