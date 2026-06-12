---
title: "Ubuntu Breezy badger 5.10  server installation for Graphical mode"
date: 2006-05-26
forum: Installation &amp; Upgrades
---

### Post by jayantha on 2006-05-26
Please tell me how to get graphical mode after installing Ubuntu Breeze Badger 5.10 on server mode after typed SERVER  and start installation. All the time when I boot it goes to text mode but I would like to work on Graphical mode.
Please help me

Thanks

Jayantha

---

### Post by aysiu on 2006-05-26
Log in and type...

For Gnome: ```
sudo aptitude update && sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
``` For KDE: ```
sudo aptitude update && sudo aptitude install kubuntu-desktop
sudo /etc/init.d/kdm start
``` For XFCE: ```
sudo aptitude update && sudo aptitude install xubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

