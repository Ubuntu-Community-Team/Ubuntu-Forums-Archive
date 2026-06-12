---
title: "Cant find hard drive"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by acmariner99 on 2008-05-28
I recently installed a version of ubuntu that allows it to run as a Windows application ([www.wubi-installer.org](www.wubi-installer.org) version 8.04). When I ran it for the first time, I could not find where my Windows hard drive is. Is this normal, or is there a way to get to my windows data.

---

### Post by erginemr on 2008-05-28
I am not sure about how Wubi works, but in a normal Hardy installation, if your Windows partitions are NTFS, then you can have them recorded into the /etc/fstab file (which auto-mounts the drives) by installing the package **ntfs-3g** from the terminal with:
```
sudo aptitude install ntfs-config
```
and then, runnunig the tool ntfs-config with:
```
Alt+F2 -> gksu ntfs-config
```
Enable the two checkmarks and restart your system.

The above trick might work for Wubi, too.

---

