---
title: "installing kde on ubuntu server edition"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by lollylegs on 2007-11-24
I have tried to install KDE and Gnome on Ubuntu server edition
eg:
sudo apt-get install KDE
and I keep getting no packacge found for both KDE & Gnome am a relatively newbie so would appreciate some experienced help
thank you
lollylegs Australia

---

### Post by forestpixie on 2007-11-24
can you post your sources list

```
cat /etc/apt/sources.list
```

---

### Post by zvacet on 2007-11-24
```
sudo nano /etc/apt/sources.list
```

add this lines

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse

Save and close.

```
sudo aptitude update
```

```
sudo aptitude install kubuntu-desktop
```

---

### Post by mekio_san on 2008-07-03
Was just browsing around.. Figured I'd post this before this thread became god awfully too long.

Go here to read the full article ( [https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE) ), but yo need to install x-window-system-core to get the GUIs to work.  That is all.

have fun in linux!  KDE4 is bad *** btw.

---

