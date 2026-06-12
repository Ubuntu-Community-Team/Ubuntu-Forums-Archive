---
title: "Grafical interface"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by gaufjell on 2007-03-27
Hey. I need some help to install a grafical interface like KDE, Gnome, etc on Ubuntu Server Edition. I am trying to write: 

sudo apt-get upgrade :This Works
sudo apt-get install gnome : This dosent work

I alway the the message that the pacakge dosent exist.
Can anyone help me??

---

### Post by sisco311 on 2007-03-27
KDE:
```
sudo apt-get install kubuntu-desktop
```
GNOME:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by gaufjell on 2007-03-27
Hmm

I don't get this to work. 

I get this message:
"can't find the package"

Is it better if i download it from internett, and install it from cd rom?

---

### Post by nyinge on 2007-03-27
> **gaufjell said:**
> Hmm

I don't get this to work. 

I get this message:
"can't find the package"

Is it better if i download it from internett, and install it from cd rom?

I think you may need to run the following first (to update the list of packages):
```
 sudo apt-get update 
```
Then, as the previous poster suggested:
For KDE desktop:
```
 sudo apt-get install kubuntu-desktop 
```
For GNOME desktop:
```
 sudo apt-get install ubuntu-desktop 
```

This is, of course, assuming you have a working internet connection.  If it still turns out bad, post the content of "/etc/apt/sources.list" file.

---

### Post by gaufjell on 2007-03-28
Okay, Then I have done it. how do i access the interface??

---

### Post by koshari on 2007-03-28
```
startx
```

---

