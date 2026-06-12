---
title: "i can not access the su"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by akashnayak on 2010-03-03
hello,
        i am a newbie 2 ubuntu ,bt iv already in luv wid it! my problem is that i can not get in2 the su mode even though im the only user (basicaly the admin).Plz help me out.

---

### Post by BenAshton24 on 2010-03-03
I presume you want to access root files?
if so, ALT+F2 and type:
```
gksu nautilus
```

If you just want to run some commands as root then just precede each command with:
```
sudo
```

---

### Post by kellemes on 2010-03-03
or **sudo -i** for (simulate initial login)-mode..

su by default will ask for a root-password, since there is no root-password set on a default Ubuntu-install, it won't work.

---

