---
title: "[SOLVED] wont update"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by senectus on 2008-10-03
The following is what I get if I try to update my install:
```
mybox@mybox-desktop:~$ sudo apt-get -f upgrade
[sudo] password for mybox: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  f-spot language-support-writing-en libpurple0 libqt4-core libqt4-gui
  libqt4-qt3support libqt4-sql pidgin pidgin-data qt4-qtconfig wine
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

```

If I use synaptic it shows me nothing if I filter on broken packages...

Any idea's how I force it to update my machine??

---

### Post by Pumalite on 2008-10-03
Try:
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by senectus on 2008-10-03
Perfect! thanks!

---

### Post by Pumalite on 2008-10-03
You are welcome. Good luck!

---

