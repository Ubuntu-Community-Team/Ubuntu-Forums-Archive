---
title: "In xserver-xorg im prompted with Indentifier Intel 915"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by swoll1980 on 2007-06-19
I have a intel 3dagp intagtated video card it uses the intel 845gv chipset intagrated controller what should I enter into xserver-xorg as the identifier? is there a way to configure this automaticley

---

### Post by kevinlyfellow on 2007-06-19
The identifier is just a name.  Everytime you need to use the device in xorg.conf, you can call it by that name.  It can be anything as long as its consistant

to configure x automatically, you can either
```
sudo dpkg-reconfigure xserver-xorg
```
or for a fully automatic installation (like when running the live cd)
```
sudo dpkg-reconfigure xserver-xorg -pcritical
```

And interestingly, if your running fiesty, you can actually run without it (but it will be automatically configured and you can't change it)

---

