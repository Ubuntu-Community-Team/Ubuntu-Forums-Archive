---
title: "how to remove KDE from lucid?"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by nhasian on 2010-03-21
last week after doing an upgrade from the update-manager (maybe it was a distribution update, i'm not sure i dont reboot for days at a time) I discovered I had lost Gnome and at the login window could only choose between xterm and KDE.  well KDE didnt successfully boot probably cause i never installed it, but i easily reinstalled gnome with:

```
sudo apt-get install ubuntu-desktop
```

I still however have KDE as a login option, and also update-manager wants to install all sorts of updates for kde like:

> 
libkephal4 libkfontinst4 libkscreensaver5 libksgrd4 libkworkspace4 libplasma-applet-system-monitor4 libplasma-geolocation-interface4 libplasmaclock4

I'm guessing all that libk* stuff and plasma is for KDE.  So what do i need to do to purge KDE from my system?

---

### Post by collinp on 2010-03-21
As Far As I Know, there's no "easy" way to remove KDE. Removing kdebase-bin and/or QT would probably take out almost all, if not all, of KDE.

That's how I did it. I haven't seen a single KDE package update since.

---

### Post by nhasian on 2010-03-23
thanks that got rid of most of it. :)

---

