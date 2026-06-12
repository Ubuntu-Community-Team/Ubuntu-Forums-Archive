---
title: "update problems"
date: 2013-06-30
forum: Installation &amp; Upgrades
---

### Post by ro12 on 2013-06-30
Hi, I get this error when I try to update in terminal```
dpkg: error: parsing file '/var/lib/dpkg/status' near line 27728 package 'rar': mixed non-coinstallable and coinstallable package instances present
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Thanks if anyone can help

---

### Post by fantab on 2013-06-30
How about:

```
sudo dpkg --purge rar
sudo apt-get remove --purge rar
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get update
```

---

