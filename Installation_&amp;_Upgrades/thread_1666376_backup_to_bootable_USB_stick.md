---
title: "backup to bootable USB stick?"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by iaw4 on 2011-01-13
I would like to back up my current system to a bootable memory stick.  (I do not want to create an image of the ubuntu installation disk.)

such a backup should not be a big problem---even after updating 350MB of ubuntu 10.04 LTS, I still have only about 3GB used.  so, it should all fit easily onto a 4GB stick.

is there a GUI or script solution that will make a full bootable backup of a running ubuntu system (incl root, etc.)?

sincerely,

/iaw4

---

### Post by sharathcshekhar on 2011-01-13
Try remastersys. It comes with a GUI as well

---

### Post by C.S.Cameron on 2011-01-13
Remastersys will backup your install to iso.
The results can be used to make a Live CD/USB which can be used to install the backup to disk.

Or you can use dd to clone the original disk to USB stick but you need to shrink the partition to a size that will fit the flash drive.

---

