---
title: "Installing XFCE on Server install"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by Rayston on 2006-09-11
> **K.Mandla said:**
> Start with a server install. Then

```
sudo aptitude install x-window-system-core xfce4
```
From there you can add whatever you like. You'll find it's much snappier than a full-blown Xubuntu installation.

Have fun!

I followed the above from a different thread. But cant actually start xfce 

when I try I get 

Xsession: unable to start X session --- no "/home/username/.xse
"/home/username/.Xsession" file, no session managers, no window terminal emulators found; aborting.

and when I try startxfce4 I get

command not found.

anyone have any ideas?

Thanx

Rayston

---

### Post by taurus on 2006-09-11
```

sudo aptitude update
sudo aptitude install xubuntu-desktop
sudo /etc/init.d/gdm start

```

---

