---
title: "W:Failed to fetch http://de.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n"
date: 2014-11-11
forum: Installation &amp; Upgrades
---

### Post by 0ll0 on 2014-11-11
U 12.04 32 bit:
W:Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en](http://de.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en)  Hash Sum mismatch

search for updates stops here. any suggestions?

---

### Post by bapoumba on 2014-11-11
Please try :
```
sudo mv /var/lib/apt/lists/* ~/Desktop/
sudo apt-get update
sudo apt-get upgrade

```
If it works, you can remove the files from your desktop.

---

