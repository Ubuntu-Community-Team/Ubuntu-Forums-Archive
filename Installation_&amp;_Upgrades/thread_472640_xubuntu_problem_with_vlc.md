---
title: "xubuntu problem with vlc"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by joelsoto1 on 2007-06-13
i try to install vlc on the p.c and it gives me this error code..    Media change: please insert the disc labeled
 'Xubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)'
in the drive '/cdrom/' and press enter
         i tryd everything and i cant figure it out.. help would be much appreciated  no idea where i can find this or any idea if it'll even help.. thanks

---

### Post by taurus on 2007-06-13
You can comment out the cdrom repo in /etc/apt/sources.list so it would install everything from the net.  

Edit /etc/apt/sources.list

```
gksudo mousepad /etc/apt/sources.list
```
and place a # in front of the line that has cdrom it it.  Save it and run

```
sudo aptitude update
sudo aptitude install vlc
```

---

### Post by joelsoto1 on 2007-06-14
thanks

---

