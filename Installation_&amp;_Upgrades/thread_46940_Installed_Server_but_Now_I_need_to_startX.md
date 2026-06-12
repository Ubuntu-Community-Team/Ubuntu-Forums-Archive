---
title: "Installed Server but Now I need to startX"
date: 2005-07-06
forum: Installation &amp; Upgrades
---

### Post by docmur on 2005-07-06
Hello.

I just reinstalled Ubuntu in server mode.  I did this because I wanted to have no graphical front, like gnome.  Instead I wanted to have fluxbox as the only usable GUI on the system.  so in order I did

apt-get install xfe
apt-get install fluxbox
apt-get install idesk

How ever when I try start xfe of start fluxbox I get an error.
I even tried to startx but it gave up and sent me back to the shell.  Does anyone know how to fix this??

---

### Post by javiadip on 2005-07-06
what's the error? post your log file

---

### Post by WildTangent on 2005-07-06
you need the x-windows system core ;)

```
sudo apt-get install x-window-system-core
```

youll also need synaptic

```
sudo apt-get install synaptic
```

and any other apps youll need, like firefox, gedit, etc

-Wild

---

