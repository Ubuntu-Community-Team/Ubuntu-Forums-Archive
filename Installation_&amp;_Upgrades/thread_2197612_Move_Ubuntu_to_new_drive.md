---
title: "Move Ubuntu to new drive"
date: 2014-01-04
forum: Installation &amp; Upgrades
---

### Post by joe-moyers on 2014-01-04
Hello, I am running Win7 Pro and Ubuntu 12.04 dual boot on a 500Gb SATA drive. I purchased a second identical 500Gb drive. I would like to move Ubuntu to the second drive and continue to dual boot this system. What would be the best way to do this? It is a new system with UEFI AMI BIOS.

---

### Post by varunendra on 2014-01-05
You can use either Gparted (can be installed from repositories, already installed on the Live CD) or a disk/partition imaging tool like 'clonezilla' to copy the partition(s) over to the other drive. Afterwards, you can simply delete the source partition and use Boot-Repair to add the cloned partition to the boot menu.

---

