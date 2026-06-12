---
title: "Wrong Hash"
date: 2016-10-27
forum: Installation &amp; Upgrades
---

### Post by valereguerin on 2016-10-27
Hello,

```
sudo apt-get update && sudo apt-get upgrade = 
W: Impossible de récupérer http://fr.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-amd64/Packages  Somme de contrôle de hachage incohérente 
``` :confused:

control checksum ?


Bye !:D

Laptop L505 13 j

---

### Post by ajgreeny on 2016-10-27
Try ```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```one by one and show us the output of each of those commands.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

It may also be worth changing the server you use for updates from the French one to the Main server which you can do in the **Software & Updates** utility.

---

