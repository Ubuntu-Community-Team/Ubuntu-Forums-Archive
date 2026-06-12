---
title: "Ubuntu 21.10 - extensions failing after upgrade"
date: 2021-10-15
forum: Installation &amp; Upgrades
---

### Post by JoelParke on 2021-10-15
Last week I upgraded one machine to 21.10 and did update, upgrade, etc.
I found Gnome 40 and all my usual extensions working - dash-to-panel, etc...

Today I upgraded FROM 21.04 on another machine; my laptop - using the standard upgrade...
BUT on this laptop, many of the extensions i use, won't work... EVEN the ones that I tested before after upgrading that first machine.

SO what could the issue be?  
For example, I install dash-to-panel, by turning it ON,
It seems to install and turn on, but it does nothing.
Refreshing the installed extensions shows that it is OFF
Installing Windows List, OpenWeather does not either???

SO that seems like some settings can not be enabled.
I tried reinstalling Gnome, etc... 
BUT no luck.

ANY Ideas?

---

### Post by MAFoElffen on 2021-10-16
Two systems. Same versions of Ubuntu. Two different hardware platforms right? So is the differences hardware based and relevant hardware driver based?

Or if you do this on both
```

sudo apt list > ~/home/Documents/packagelist.txt

```
Then do a "dif" on both to compare them (while the files are accessed from the same location), maybe there is a package difference between the two?

Just ideas...  That is what I would try first.

---

