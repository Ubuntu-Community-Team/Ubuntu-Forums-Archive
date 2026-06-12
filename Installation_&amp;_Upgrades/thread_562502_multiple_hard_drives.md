---
title: "multiple hard drives"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by ats1080s on 2007-09-28
im trying to install server edition on a computer with 4 hard drives.  1 250GB SATA drive, 1 80GB IDE drive and 2 40GB IDE drives.  what i want to do here is make one lvm partition for all 4 drives so there is no confusion for me which files are on what hard drives.  i did the option to install lvm but it only formatted 1 disk.  2 of the disks still had windows and one had suse.  but anyway, what did i miss?  last time i did an lvm install was using clark connect and i did the same guided setup for that and it worked like a dream.

---

### Post by Pumalite on 2007-09-28
Post:
sudo fdisk -lu
(with Live CD if you have to)

---

