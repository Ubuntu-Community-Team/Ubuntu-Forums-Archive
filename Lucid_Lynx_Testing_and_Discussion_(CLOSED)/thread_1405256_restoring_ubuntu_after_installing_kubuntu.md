---
title: "restoring ubuntu after installing kubuntu"
date: 2010-02-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-02-12
i have tried to install kubuntu and i don't understand what people like so much about it any way i have some 
problems after removing it one is the logon screen not returning to default two the log off button doesn't work and third i have a lot new pacages to check and remove but i was thinking of something eles i still have 
the previous kernel version 12 can i use it to restore ubuntu?

thanks in advance.

---

### Post by Kenny_Strawn on 2010-02-12
Ubuntu and Kubuntu are two different distros, but if you mean installing GNOME instead of KDE:

```
sudo apt-get install ubuntu-desktop && sudo apt-get autoremove --purge kubuntu-desktop
```

---

### Post by aviramof on 2010-02-12
thanks for your help

---

