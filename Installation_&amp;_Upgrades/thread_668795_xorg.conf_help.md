---
title: "xorg.conf help"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by what22 on 2008-01-15
Today I attempted to install Ubuntu 7.10 on my friends laptop (older Acer Travelmate). When we finished installing, which we had to do by pulling the hard drive out and installing on another machine, it would only boot into the terminal. I looked and the xorg.conf says the wrong video card. Is there any way to make the computer auto-configure the current card or must it be manually changed?

---

### Post by kostkon on 2008-01-15
You can auto-configure the card by giving
```
sudo dpkg-reconfigure xserver-xorg
```

Follow and complete all the steps of the configuration and you should be fine.

---

### Post by RockHaxor on 2008-01-15
In the terminal,  type


```
sudo rm /etc/X11/xorg.conf.*
```

this should do the trick

Good Luck!

---

