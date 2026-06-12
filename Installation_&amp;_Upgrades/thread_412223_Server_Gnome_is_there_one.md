---
title: "Server Gnome is there one????"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by keiffee30 on 2007-04-17
i have installed ubuntu server and its working lovely. The only problem i have is that im not used to a command/shell type interface. Is there a way to install a X11/Gnome/KDE interface so it can be made more user frendly

---

### Post by taurus on 2007-04-17
Just do

```
sudo aptitude update
sudo aptitude install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by keiffee30 on 2007-05-06
ok many thanks, i have now tried this and its wkring like a dream now. many thanks for your help in this post

---

