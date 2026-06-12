---
title: "RAID disk orders question"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by atlantakid on 2011-09-23
Hello, I am not new to RAID and LVM but am new to Linux/Ubuntu RAID, my questions are:
A.  If I create a raid using "mdadm --create /dev/md1 --level=5 --raid-devices=3 /dev/sda2 /dev/sdb2 /dev/sdc2" does MDADM saves disks order somewhere on the disks, if the SATA cables are disconnected and re-connected in a different order /dev/sd?? gets reordered, does the RAID handle it OK using some sort of internal UID?

B. I am trying to reverse engineer a Iomeg SAN storage, they are using RAID 5 for the data portion, the mdadm package is on the appliance but I can not find mdadm.conf!  Is there a way to configure and operate RAID without having mdadm.conf, is it possible to use a different filename and somehow tell the RAID driver to use that config file instead?

Any sort of pointer will be great.
Thank you.

---

