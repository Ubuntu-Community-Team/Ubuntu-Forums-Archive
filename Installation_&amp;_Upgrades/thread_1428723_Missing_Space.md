---
title: "Missing Space"
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by jimmers on 2010-03-13
Hi All,
Using the USB Startup Disk Creator in Karmic, I installed Jaunty on a 16 GB Pen Drive,
Where it says Documents and Settings will be saved in Reserved Space, it only shows 4GB,
my question where is the missing space??
The pen drive was formatted to Fat32, is there a Command Line script to to find said missing Space.

As usual all help, suggestions, ideas greatly appreciated.

---

### Post by phillw on 2010-03-13
> **jimmers said:**
> Hi All,
Using the USB Startup Disk Creator in Karmic, I installed Jaunty on a 16 GB Pen Drive,
Where it says Documents and Settings will be saved in Reserved Space, it only shows 4GB,
my question where is the missing space??
The pen drive was formatted to Fat32, is there a Command Line script to to find said missing Space.

As usual all help, suggestions, ideas greatly appreciated.

Casper (the bit that looks after saving the files) is limited by the FAT32 filesystems' maximum 4GB file-size.

You can partition the usb stick to give, say 11GB, to an ext3 or ext4 filesystem (or even ntfs). Call it something like data and you'll be able to store videos etc on that partition. A bit like having a seperate home partition.

Regards,

Phill.

---

### Post by jimmers on 2010-03-14
Thanks Phil, will give it a go.

---

