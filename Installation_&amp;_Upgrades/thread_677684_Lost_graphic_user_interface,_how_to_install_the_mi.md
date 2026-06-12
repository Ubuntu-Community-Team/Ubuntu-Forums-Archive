---
title: "Lost graphic user interface, how to install the minimum requirement?"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by rockballad on 2008-01-25
Hello there,

During the last upgrading, my laptop down. So after that, I can't login to Ubuntu with Graphic User Interface. Please tell me how to restore or install it again? Thanks very much!

---

### Post by zvacet on 2008-01-25
```
startx
```

or 

```
sudo /etc/init.d/gdm start
```

---

### Post by rockballad on 2008-01-25
> **zvacet said:**
> ```
startx
```

or 

```
sudo /etc/init.d/gdm start
```

Thank you! Command startx brings me to a white-blank screen. Could you please tell me why?

Every apt-get install ... returns an error at the end: broken package although I run apt-get update --fix-missing

---

### Post by zvacet on 2008-01-25
If you have broken packages

```
sudo apt-get -f install
```

---

### Post by rockballad on 2008-01-27
I did it, and nothing to install, update or remove. 

Is there a way to install from the begin but not clean up the existing Ubuntu? I installed Maemo 3.2 on this machine. It took a long time so I don't want to do it again. I want to keep it during the new installation of Ubuntu. How can I do, please tell me. Thanks very much!

---

### Post by zvacet on 2008-01-28
Try this command to fix broken packages

```
sudo dpkg --configure -a
```

---

### Post by zvacet on 2008-01-28
Maybe one other option is 

if you use GNOME

```
sudo apt-get install --reinstall ubuntu-desktop
```

for KDE

```
sudo apt-get install --reinstall kubuntu-desktop
```

---

### Post by PmDematagoda on 2008-01-28
The issue may be something to do with the configuration of your X-Server. Try:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Also, could you please post the specifications of your PC.

---

### Post by rockballad on 2008-01-29
> **zvacet said:**
> Maybe one other option is 

if you use GNOME

```
sudo apt-get install --reinstall ubuntu-desktop
```

for KDE

```
sudo apt-get install --reinstall kubuntu-desktop
```

Thank you. I'm using GNOME.

```
sudo apt-get install --reinstall ubuntu-desktop
```

This returns the msg: package ubuntu-desktop has no installation candidate
I did some searching but got no result.

PmDematagoda, the cmd ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` seems to reconfigure the xserver? After doing that, I startx but all I got is error: no screen found. The last time, when I startx'ed, it was a blank while screen :confused:

If there's no other way, I'll reinstall. Thank you all, a lot!

---

### Post by Subetealabici on 2008-01-30
Hey HO

  I have a similar problem with some library that i dont now the name, but all the caracters at the gdm disapear and there is only a kind off cubes??, how can I repair that??.

---

### Post by zvacet on 2008-01-31
```
cat /etc/apt/sources.list
``` 

Post it here.

---

