---
title: "Not too fond of sudo"
date: 2005-05-03
forum: Installation &amp; Upgrades
---

### Post by sprucio on 2005-05-03
I know the concept of sudo and I see that Ubuntu has decided to use this. I've re-activated the root account with a password but I still can't use the root password to do many things. For example, when I go to do some system changes in GNOME or KDE, it'll prompt me for a password. Here, if I use the root password, nothing happens. On the other hand, if I use the password of the initial user that was created during installation, it works fine.

I guess Ubuntu by default gives admin rights to the initial user created during installation but how can I revert to the older method of Linux?

---

### Post by Nis on 2005-05-03
[QUOTE=sprucio]I know the concept of sudo and I see that Ubuntu has decided to use this. I've re-activated the root account with a password but I still can't use the root password to do many things. For example, when I go to do some system changes in GNOME or KDE, it'll prompt me for a password. Here, if I use the root password, nothing happens. On the other hand, if I use the password of the initial user that was created during installation, it works fine.

I guess Ubuntu by default gives admin rights to the initial user created during installation but how can I revert to the older method of Linux?[/QUOTE]
 Anything in GNOME that asks for your password (a la sudo) is using gksudo.  You can edit the *.desktop files to change the gksudo part to gksu and you should get the traditional way back.  Not sure how to do this in Kubuntu.

---

### Post by sprucio on 2005-05-05
Is there a way to turn this off during installation?

---

### Post by arnieboy on 2005-05-05
refer to [http://ubuntuforums.org/showthread.php?t=31053](http://ubuntuforums.org/showthread.php?t=31053) if u are too frustrated with sudo but be careful..

---

