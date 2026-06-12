---
title: "[SOLVED] Changing Distrobutions without grub 22"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by Deadmode on 2008-07-18
Hi, I'd like to change my linux distro xubuntu to ubuntu, but don't want to run into problem of grub error 22 (invalid partition). Thanks :)

---

### Post by PmDematagoda on 2008-07-18
Just install the ubuntu-desktop package with:-
```
sudo apt-get install ubuntu-desktop
```
that should install Ubuntu(it's really just a set of packages) without causing any problems with GRUB. You should choose GNOME as the default session after install ubuntu-desktop in order to use it, otherwise you will login to Xfce instead of GNOME.

---

### Post by Deadmode on 2008-07-20
thank u that was very helpful :)

---

