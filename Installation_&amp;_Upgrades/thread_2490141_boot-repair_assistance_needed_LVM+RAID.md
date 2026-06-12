---
title: "boot-repair assistance needed LVM+RAID"
date: 2023-08-23
forum: Installation &amp; Upgrades
---

### Post by sstech27 on 2023-08-23
boot-repair installed on a USB drive wants to install the MBR to sda (which is the usb drive). Could an expert take a look at this and let me know what i'm missing please. Thanks

UPDATE: disregard, issue solved by creating a temporary USB boot device to get the operating system running to repair the grub configuration after an LVM change

---

### Post by MAFoElffen on 2023-08-24
Further Recommendations:

This is a new install of 2 4TB drives as RAID1, booted by Legacy MBR , with an MBR ms-dos partition table... There are some limitations there, which you are pushing the boundaries of. 

I would have partitioned as GPT partition tables, which to boot MBR Legacy, have required that you add bios_boot partition(s) (x2, because it is mirrored). Second recommendation would be to separate the /boot folder out to it's own partition, outside the LVM, as ext4.

---

