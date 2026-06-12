---
title: "upgrade and rollback"
date: 2018-06-08
forum: Installation &amp; Upgrades
---

### Post by sacarde on 2018-06-08
hi,
   is there a method to do an upgrade and, if somethings go wrong, return at previous situation ?





thank you

---

### Post by Impavidus on 2018-06-08
Restore a backup of your entire system, if you have one.

I don't keep backups of my entire system (only of my documents). When an upgrade breaks it, I fix it somehow or I make a fresh install. I always keep a live disk ready. But I've been using Ubuntu for almost 12 years now and I've encountered a bad upgrade only once, which I could fix using a live disk. Creating weekly system backups that save me an hour once every ten years just isn't worth the effort.

Kernel upgrades are slightly different. They're more likely to go wrong (never happened to me though), but when a new kernel is installed, the old one isn't automatically removed, so you can simply boot the old kernel until a fix is available.

Release upgrades, from one version of Ubuntu to the next, are different. If one of those goes wrong, the best option is a fresh install.

---

### Post by sacarde on 2018-06-08
I thought it was there a script that by reading apt-log, undo packages by packages and re-installing old version from packages cache



thank you



p.s.
or use snapshot if filesystem permits

---

