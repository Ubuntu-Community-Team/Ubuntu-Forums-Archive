---
title: "Restoration of Backups after Migration to Ubuntu 18.04 (Bionic Beaver)"
date: 2018-07-23
forum: Installation &amp; Upgrades
---

### Post by jmacharia07 on 2018-07-23
Hi, 
I recently upgraded from Ubuntu 14.04 to 18.04. I followed the procedure of Backing up Data using Deja Dup but after installing Ubuntu 18.04 some issues cropped up:-
1) I realized the during the installation process Ubuntu 18.04 will not allow one to upgrade from a prior version with Data. i.e. Your Data will be Deleted!
2) After Installation of Bionic Beaver it will not allow one to restore Backups from 14.04.
3) If your try installing Systemback it informs that it is not supported on 18.04
4) If you try installing Aptik the same happens once it gets to the thread on Systemback Error 404 occurs.

I urge the Ubuntu community to try a find a way around the same as this is a nightmare. We rely on Ubuntu for Data Integrity!!:(

---

### Post by TheFu on 2018-07-23
Booting from alternate media is a quick fix for all sorts of issues.

Boot from a 14.04 flash drive/ISO, mount the storage for both the target and the source, then use dejadup to restore the data.

---

