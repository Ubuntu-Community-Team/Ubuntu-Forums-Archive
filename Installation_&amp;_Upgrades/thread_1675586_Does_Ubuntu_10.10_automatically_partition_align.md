---
title: "Does Ubuntu 10.10 automatically partition align?"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by Stibbs on 2011-01-25
I've recently bought a new laptop with a Kingston 128gb SSD, which came preloaded with Windows 7. I'm looking to wipe it completely (Not quite sure how to do this, although that's not the main question of this thread) and install Ubuntu on it.

After some researching yesterday, I've learned that for an SSD to work at it's maximum potential you want to have the partition start after one complete block. (Or at least that's how I understood it)

Does Ubuntu automatically configure its partitions to do this upon install? After a quick search it looks like it was going to be but I never really saw a concrete answer.

Thanks in advance!

---

### Post by srs5694 on 2011-01-25
I'm pretty sure that Ubuntu 10.10 does align partitions properly on installation; however, to be sure, you should check it using a tool such as fdisk -- type "sudo fdisk -lu" at a shell prompt and verify that the partitions' start sector values are all divisible by whatever value is appropriate for your device. (2048 works well with most devices.) You may need to interrupt the installation and reboot into live CD mode to test this; or you could just let it install and verify it after you've installed, planning to re-install if that proves necessary.

---

### Post by Stibbs on 2011-01-25
Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00075e24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   239822847   119910400   83  Linux
/dev/sda2       239824894   250068991     5122049    5  Extended
/dev/sda5       239824896   250068991     5122048   82  Linux swap / Solaris

sda5 is divisible. sda2 seems almost pointless?

---

### Post by srs5694 on 2011-01-25
Don't worry about your /dev/sda2; it's an extended partition, which is just a carrier for logical partitions such as /dev/sda5, so it (/dev/sda2) needn't follow the usual alignment rules.

---

