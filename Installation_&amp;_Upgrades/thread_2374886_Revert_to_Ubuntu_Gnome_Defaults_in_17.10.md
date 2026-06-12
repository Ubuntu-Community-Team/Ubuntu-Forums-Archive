---
title: "Revert to Ubuntu Gnome Defaults in 17.10"
date: 2017-10-20
forum: Installation &amp; Upgrades
---

### Post by mrkeef on 2017-10-20
So I did the upgrade to 17.10 and everything is looking good.

I was using Gnome in 17.04 with a few changes Dash To Dock, some apps and so on, theme.

I found that the upgrade has kept my modifications which is nice, but when I log in to the Ubuntu session it also has my modified Gnome set up rather than the standard Ubuntu version.Is it possible to force the Ubuntu session to use the defualt Ubuntu settings and keep my original settings in the Gnome session?

---

### Post by dino99 on 2017-10-20
first clean the system: gtkorphan & bleachbit (as root)
then, use Settings (control-center) /dconf (dconf-editor)/tweaks (gnome-tweaks-tools)

---

