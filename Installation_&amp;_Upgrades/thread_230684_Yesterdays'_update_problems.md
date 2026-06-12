---
title: "Yesterdays' update problems"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by bebe on 2006-08-06
Helo,

Yesterday i upgrade my entire system. It is official Ubuntu upgrade, Gnome 2.14.3 and so on. After the reboot I encountered some problems with gnome-panel (there are no icons in menus). When I launch gnome-theme-manager window pops up and it says that metacity is not there or gconf is broken.

So what should I do? I do not install any other packages that that upgrade, so it is virgin Dapper :)

Bartek

---

### Post by tseliot on 2006-08-06
Try with:
```
sudo apt-get update
```

```
sudo apt-get install -f
```

```
sudo apt-get dist-upgrade
```

---

### Post by bebe on 2006-08-06
What are You talking about?
There are no new packages to install. Read My post and then help me. After update something went wrong with icons on gnome panel, etc.

---

