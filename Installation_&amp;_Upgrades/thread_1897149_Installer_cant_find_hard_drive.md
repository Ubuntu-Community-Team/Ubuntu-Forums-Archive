---
title: "Installer cant find hard drive"
date: 2011-12-18
forum: Installation &amp; Upgrades
---

### Post by Rickbmw on 2011-12-18
When trying to install the latest (Ubuntu 11) the installer cannot find any hard drives although win7 boots just fine.  When I connect an external USB drive the installer finds both the external and the internal drives but cant detect a windows installation.  Trying to install a dual boot.  Any ideas?

---

### Post by darkod on 2011-12-18
The most common reason the installer not to see a disk as present is if it was used in RAID earlier and it still has the meta data present (formatting doesn't remove it). Windows doesn't mind this, but ubuntu doesn't let you install not knowing if you use raid or not.

If you are NOT running raid (and ONLY IN THIS CASE), boot in live mode and in terminal do:
sudo dmraid -E -r /dev/sda

Usually /dev/sda would be your internal hdd. If that asks you to confirm meta data removal, say yes and problem solved.

Note that if you are running raid that command will destroy your array!!!

---

