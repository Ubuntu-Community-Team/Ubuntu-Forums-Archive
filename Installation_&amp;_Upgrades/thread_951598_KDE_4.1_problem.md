---
title: "KDE 4.1 problem"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by lio_013 on 2008-10-18
after  upgrading to ubuntu 8.10 beta version gnome works good but when i log into kde i have this error 

"the desktop entry file 
/home/myname/.kde/autostart/awn.desktop  has no type=... entry."
when i click the ok button of this error message the ubuntu  log off so i had to login to gnome and post this
any ideas???????????????

---

### Post by gjoellee on 2008-10-18
you can try to remove AWN and see if you get this error

if it doesn't help do this:
in GNOME do this:
open terminal and type:
```
sudo apt-get remove kde* && sudo apt-get install kubuntu-desktop
```

---

### Post by lio_013 on 2008-10-18
if i try to reinstall kde 
i wont be have to redownload all the kde packages.....righ?

---

