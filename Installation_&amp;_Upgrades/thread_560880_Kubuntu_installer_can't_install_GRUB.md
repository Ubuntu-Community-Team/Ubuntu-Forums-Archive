---
title: "Kubuntu installer can't install GRUB"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by BrokeBody on 2007-09-26
[http://img165.imageshack.us/img165/9062/snapshot1hr6.png](http://img165.imageshack.us/img165/9062/snapshot1hr6.png)

This the first time it can't install it. Now what?

---

### Post by Pumalite on 2007-09-26
One has to suspect sda1. What happened there?
Do you have access to a Linux system? if so, post:
sudo fdisk -lu
If nor, get a Knoppix and let's take a look: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
(is there a 'rescue partition' there?)

---

