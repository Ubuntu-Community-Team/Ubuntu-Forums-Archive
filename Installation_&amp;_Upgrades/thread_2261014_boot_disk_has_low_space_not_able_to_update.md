---
title: "boot disk has low space not able to update"
date: 2015-01-15
forum: Installation &amp; Upgrades
---

### Post by Denbid on 2015-01-15
The upgrade needs a total of 60.9 M free space on disk '/boot'. Please free at least an additional 11.1 M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean

I'm using ubuntu 14.04 LTS

---

### Post by grahammechanical on 2015-01-15
Have you done what has been suggested? Have you emptied the Trash can and also run?

```
sudo apt-get clean
```

At the Grub boot menu we can select Advanced options for Ubuntu in the sub-menu we select Recovery mode. At the recovery menu we can select Clean. That will run two commands apt-get clean and apt-get autoremove. That should create some free space. Do empty the trash.

Regards.

---

### Post by Impavidus on 2015-01-16
Try removing some old kernels:```
sudo apt-get autoremove --purge
```

---

### Post by efflandt on 2015-01-16
What does the following show for your /boot partition or whatever partition it is on? You either need to clean house or use a bigger /boot.```
df -h
```

---

