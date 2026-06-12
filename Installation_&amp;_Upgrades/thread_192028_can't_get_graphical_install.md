---
title: "can't get graphical install"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by not_yet on 2006-06-08
I go through the entire install procedure, remove the disk and reboot

I then get a text only login ?

---

### Post by JSchwage on 2006-06-08
Try typing "startx" after you've logged in and let me know what happens. Also, did you use the Live CD to install or the alternate one?

---

### Post by taurus on 2006-06-08
Sounds like maybe you downloaded and installed the server version!!!  If that's the case, then you need to install either Gnome, KDE, or even XFce as your window manager.
```

sudo apt-get install ubuntu-desktop <-- for Gnome
sudo apt-get install kubuntu-desktop <-- for KDE
sudo apt-get install xubuntu-desktop <-- for XFce

```

---

### Post by not_yet on 2006-06-08
thanks, I guess I installed the wrong version

installing gnome with apt-get as taurus suggested:mrgreen: 

cheers

---

