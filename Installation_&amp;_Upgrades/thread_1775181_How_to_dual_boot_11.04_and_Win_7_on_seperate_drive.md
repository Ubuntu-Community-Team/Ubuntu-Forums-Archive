---
title: "How to dual boot 11.04 and Win 7 on seperate drives"
date: 2011-06-04
forum: Installation &amp; Upgrades
---

### Post by _joecrawford on 2011-06-04
So I have Ubuntu 11.04 on 1TB HDD and Win 7 on another 1TB HDD. Right now I have to unplug a SATA cable to get to boot into one or the other. What is the best way to be able to pick. I don't care which OS I do it in or which is the primary, if there has to be one. I have an MSI mobo. Thanks!

---

### Post by _joecrawford on 2011-06-04
If it helps, they are both 64 bit OS.

---

### Post by oldfred on 2011-06-04
Plug them both in and make sure the windows one is in the lower port number so it is sda (drive 0 in windows). Windows does not like drive changes.

Ubuntu will tolerate drive changes as it first looks for drive and if not found then search by UUID.

Change BIOS to boot sdb, your Ubuntu drive.

sudo update-grub

That will find your windows install and let you boot it from the grub menu. Then you do not have to plug or unplug drives. But if you ever do unplug, they are still bootableable on its own.

---

