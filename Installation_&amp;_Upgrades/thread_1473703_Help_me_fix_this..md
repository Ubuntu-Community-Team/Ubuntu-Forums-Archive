---
title: "Help me fix this."
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by charles_shipp on 2010-05-05
Every time I update my system I get theses errors.E:nautilus:dependency problems-leaving unconfigured 
E:gnome-settings-daemon:dependency problems-leaving unconfigured
E:libgnome-window-settings1:dependency problems-leaving unconfigured
E:gnome-control-center:dependency problems-leaving unconfigured
E:compiz-gnome:dependency problems-leaving unconfigured
E:gnome-panel:dependency problems-leaving unconfigured
E:gnome-session:dependency problems-leaving unconfigured
E:gnome-applets:dependency problems-leaving unconfigured
E:compiz:dependency problems-leaving unconfigured
E:eog:dependency problems-leaving unconfigured
E:evolution:dependency problems-leaving unconfigured
E:evolution-couchdb:dependency problems-leaving unconfigured
E:evolution-exchange:dependency problems-leaving unconfigured
E:evolution-plugins:dependency problems-leaving unconfigured
E:gnome-screensaver:dependency problems-leaving unconfigured
E:indicator-applet:dependency problems-leaving unconfigured
E:indicator-applet-session:dependency problems-leaving unconfigured
E:nautilus-share:dependency problems-leaving unconfigured
E:python-gnomedesktop:dependency problems-leaving unconfigured
E:python-gnome2-desktop:dependency problems-leaving unconfigured
E:ubuntu-desktop:dependency problems-leaving unconfigured
E:evolution-indicator:dependency problems-leaving unconfigured

---

### Post by kansasnoob on 2010-05-05
Try running the command:

```
sudo dpkg --configure -a
```

If that also fails try:

```
sudo apt-get clean
```

And again:

```
sudo dpkg --configure -a
```

Or after running "apt-get clean" try updating again.

---

### Post by charles_shipp on 2010-05-17
I tried and still get the same thing.

---

### Post by kansasnoob on 2010-05-17
Follow the advice in your other thread:

[http://ubuntuforums.org/showthread.php?t=1473696&page=2](http://ubuntuforums.org/showthread.php?t=1473696&page=2)

Multiple threads only create confusion :)

---

### Post by NUboon2Age on 2010-05-17
Does Synaptic show any Broken Packages?  If so run 'Fix Broken Packages' from the edit menu, and then 'Apply'

---

### Post by kansasnoob on 2010-05-17
> **NUboon2Age said:**
> Does Synaptic show any Broken Packages?  If so run 'Fix Broken Packages' from the edit menu, and then 'Apply'

Good idea!

---

### Post by charles_shipp on 2010-05-17
Where Synaptic?

---

