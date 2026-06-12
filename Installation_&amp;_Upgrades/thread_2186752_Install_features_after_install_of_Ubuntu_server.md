---
title: "Install features after install of Ubuntu server"
date: 2013-11-08
forum: Installation &amp; Upgrades
---

### Post by Josh_Mustillo on 2013-11-08
Hello,

Installing Ubuntu Server on VirtualBox on my PC just to play around with, but on the select features page I accidentally pressed enter without installing things that I wanted, so is it possible to install things like, OpenSSH, Mail Server after the installation of Ubuntu Server?

Thanks,

Mustillo

---

### Post by steeldriver on 2013-11-08
If you want to be presented with the same menu-based choice again, you can run tasksel at any time

```
sudo tasksel
```

Otherwise, if you know what package(s) you want to install, you can do so individually e.g.
```
sudo apt-get install openssh-server
```
or
```
sudo apt-get install lamp-server^
```

---

### Post by Josh_Mustillo on 2013-11-08
Thank you very much! I did get promoted with that screen again but silly question how do I select which ones I want? If I push enter it goes on to the next screen.

---

### Post by heir4c on 2013-11-08
Use the Space bar.

---

### Post by steeldriver on 2013-11-08
try spacebar

---

### Post by Josh_Mustillo on 2013-11-08
Thanks guys! appreciate it

---

