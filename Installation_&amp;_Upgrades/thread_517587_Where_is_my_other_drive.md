---
title: "Where is my other drive?"
date: 2007-08-04
forum: Installation &amp; Upgrades
---

### Post by sieg on 2007-08-04
We are installing Ubuntu 6.06 on a USB HDD connected to a new Vista notebook PC.

I want to use DD to backup the vista partition on the internal boot drive to a partition on the USB HDD.

However, when I boot Ubuntu from the USB HDD, "fdisk -l" only lists /dev/sdb which is the external USB HDD.

I tried fdisk /dev/hda -l and fdisk /dev/sda -l and fdisk /dev/sdc -l but nothing worked.

When I booted knoppix, it had the same symptoms. The installation procedure was able to see the internal drive. Why cannot I see it from the fdisk?

Thanks,
Siegfried

---

### Post by benx009 on 2007-08-04
post your /etc/fstab plz

---

### Post by sieg on 2007-08-06
Since ubuntu does not recognize my network card and I could not figure out how to write to a flash ram stick, I'm typing the contents of /etc/fstab by  in by hand:

/dev/sdb1 / ext3 defaults,errors-remount -r 0 1
/dev/sdb5 none swap sw 0 0
/dev/hda /media/cdrom0 udf,iso9668 user,noauto 0 0

---

