---
title: "Install bootloader on /"
date: 2013-10-25
forum: Installation &amp; Upgrades
---

### Post by Azyx on 2013-10-25
Hey. I have made an upgrade from Ubuntu 10.04 32-bit to 12.04 64bit and inte the process a seem to have installed the bootloader on a spare partition, that I now want to think and move over to /home.. My problem is that I already have **/**, **/home**, **swap** and the **spare partition** as primary partition (the maximun 4 partition). So I'm not able to make a 5th on the hdd as one guide recommend.

How will I do to install grub 2 bootloader preferably on /-partition?

/Cheers

PS. I have a usb-live disk I can boot from

---

### Post by Azyx on 2013-10-25
Ahh. Checked with Gparted from LiveUSB that my swap by some reason was boot-flagged. I just changed the boot-flag to /-partition and it works fine :)

/Cheers

---

