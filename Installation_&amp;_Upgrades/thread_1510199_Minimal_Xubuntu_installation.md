---
title: "Minimal Xubuntu installation"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by DanMachado on 2010-06-15
Hi everybody,

I did a minimal Xubuntu 9.04 installation. However when I try:
 ```
$ sudo apt-get install xorg
```I get the message: 

```
E: Couldn't find package xorg
```(Please bear in mind that it is a Command-line system) At the time I did the installation I did not have internet connexion.

Any suggestion?

Regards.

Dan

---

### Post by cariboo on 2010-06-16
IF you install the xfce4 meta package, it will install xorg, if you don't want to do that, try:

```
sudo apt-get install xserver-xorg
```

should do the trick.

---

