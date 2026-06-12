---
title: "Install from source.."
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by limestone on 2010-01-16
Hi! I been trying to install from source to a specifyd directory.. Ex. totem.tar.gz
./configure --prefix=/home/usr/Desktop/totem. And everything works fine and it installs with the usual make, make install.. BUT! afterwards i can't run the app.. I go into /Desktop/totem/share/applications and try to run totem.desktop but it wont work, why? do i have to install it in the original folder? I can run the /Desktop/totem/bin/totem but i want to run the .desktop file... plz help! (I'm using Ubuntu atm but will also run this at arch).

---

### Post by snowpine on 2010-01-16
Totem is in the Ubuntu repositories.

```
sudo apt-get install totem
```

should do the trick. :)

---

### Post by limestone on 2010-06-12
> **snowpine said:**
> Totem is in the Ubuntu repositories.

```
sudo apt-get install totem
```should do the trick. :)

I know that, I just played around with the source prefix tool

---

