---
title: "panels no longer transparent?"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by geokok1981 on 2008-10-27
I did a fresh installation of 8.10 rc and really liked the 
transparent panels. However as soon as I updated my system
the panels were no longer transparent. Did I do something
wrong or were the new panels ditched?
I hope not cause even a small change is better than no change at all.

---

### Post by rudenko_ruslan on 2008-10-27
> **geokok1981 said:**
> I did a fresh installation of 8.10 rc and really liked the 
transparent panels. However as soon as I updated my system
the panels were no longer transparent. Did I do something
wrong or were the new panels ditched?
I hope not cause even a small change is better than no change at all.
File "panel_bg.png" was removed in "human-theme" package 0.28.5 ([according to this]("https://launchpad.net/ubuntu/+source/human-theme/0.28.5")). But you can manually add this file from [0.28.4 package]("https://launchpad.net/ubuntu/intrepid/+source/human-theme/0.28.4/+files/human-theme_0.28.4.tar.gz") to /usr/share/themes/Human

---

