---
title: "Trouble with tribbles"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by doondoon on 2008-02-08
Okay, I'm trying to install and configure Compiz fusion and have gotten to the point it is asking:Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)'
I downloaded the install software from ubuntu but it didn't work. I'm trying one from another mirror site. If that doesn't work how can I save the work in the shell so that I don't have to start all over again.

---

### Post by taurus on 2008-02-08
Edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of the first line, cdrom, to comment it out so it won't ask you to insert the CD when you want to install something.  Then, remove the # from all the lines that start with **deb** & **deb-src**.  Save it and run

```
sudo apt-get update
```
Now, see if you can install compiz-fusion or whatever else you want.

---

