---
title: "Install Kubuntu and Ubuntu together using Live CD"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by iampriteshdesai on 2008-08-06
I want to Install Kubuntu and Ubuntu together using Live CD. Using Wubi. I have Ubuntu hardy installed using Wubi. I am trying to install Kubuntu using Live CD. I cannot download so much. Plz halp. Both live CD's are of Hardy.If i try to install kubuntu it tries to uninstall Ubuntu.

---

### Post by iaculallad on 2008-08-06
> **iampriteshdesai said:**
> I want to Install Kubuntu and Ubuntu together using Live CD. Using Wubi. I have Ubuntu hardy installed using Wubi. I am trying to install Kubuntu using Live CD. I cannot download so much. Plz halp. Both live CD's are of Hardy.If i try to install kubuntu it tries to uninstall Ubuntu.

You can use your aptitude to install your KDE Desktop instead:

```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

---

### Post by iampriteshdesai on 2008-08-06
I have slow internet and hence I have ordered the Live CD.

---

### Post by iaculallad on 2008-08-06
Actually, you can't use the Live Desktop CD to install (k)Ubuntu in your Ubuntu machine. Remember that LiveCD's are considered "complete" desktop clone installation so it tends to remove/format the drive/partition where you want it installed. I would suggest using the Alternate CD instead if it could be done. If not,your last option would be using the net.

---

