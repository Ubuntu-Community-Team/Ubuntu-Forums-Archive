---
title: "Dual boot ubuntu and backtrack 3"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by vze57gc8 on 2008-08-23
I"ve sucessfully installed ubuntu 8.04. i want to do a dual boot with backtrack 3 beta so i shrunk my ubuntu partition setting aside 4GB for bk. the problem is i dont know what to do next and i dont want to run the instillation and overwrite ubuntu. the 4BG space is listed as unallocated. a snapshot of gparted is attached. many thanks in advance

---

### Post by Pumalite on 2008-08-23
Install backtrack and then reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by vze57gc8 on 2008-08-23
i'm a little clearer as to what the issue is. Ubuntu installs as sda while backtrack installs as hda. i formatted the to be space for backtrack as ext3 thus making the partition sda. any ideas as to what to do?

---

### Post by Pumalite on 2008-08-23
Install backtrack and then reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
It doen't matter where you install backtrack. The important thing is to reinstall Grub. Different distros see the hard drives differently, but it is the same.

---

