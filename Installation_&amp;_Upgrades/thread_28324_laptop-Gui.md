---
title: "laptop-Gui"
date: 2005-04-19
forum: Installation &amp; Upgrades
---

### Post by safud on 2005-04-19
I just installed hoary on my laptop and no gui.  How do I hand install the gui?

TIA

safud

---

### Post by accuser on 2005-04-19
You mean you booted the installation cd with the server option?

Do this, for GNOME:
```
sudo apt-get install ubuntu-desktop
```

or this, if you want KDE:
```
sudo apt-get install kubuntu-desktop
```

---

### Post by safud on 2005-04-19
Got it

dpkg-reconfigure xserver-xorg

Thanks Everyone

---

