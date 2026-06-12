---
title: "uninstall 7.04 and install 8.04"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by sherlockmz on 2008-05-10
Hi
I m using dual boot, Ubuntu 7.04 and XP
i'm trying to install 8.04 and i dont know what to do.
 Any hints please

---

### Post by Pumalite on 2008-05-10
You can install Hardy on top of the 7.10. Go Manual and choose the old partitions. Ignore /swap. The installer will do the rest. You'll have a new Grub and continue to have dual boot.

---

### Post by sherlockmz on 2008-05-10
Hi
the problem is in the choose the old partition
i have
/dev/sda5 swap 1579 MB
/dev/sda6 ext3 98 MB
/dev/sda7 ext3 19683 MB

when i select sda7 and click next i have this information
[COLOR="Red"]No root file system is defined
Please correct this from the partitioning menu[/COLOR]

---

### Post by Pumalite on 2008-05-10
You have to delete each partition and make a 'New' one of the same size and assign the mount point. Example: 'root' or '/' is /

---

### Post by KamuiX on 2008-05-10
sorry but it isn't possible to upgrade 7.10 to 8.04 through the package manager?

---

### Post by Pumalite on 2008-05-10
Sure:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by sherlockmz on 2008-05-10
Hi
at partition sda7 a choose in the mount point / 
but the "error" still

what can i do?

---

### Post by sherlockmz on 2008-05-10
problem solved

---

### Post by Pumalite on 2008-05-10
I'm glad you got it working.

---

