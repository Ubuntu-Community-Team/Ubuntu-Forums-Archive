---
title: "Seg faults on update"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by nardis_Miles1 on 2006-12-21
I am getting consistent segfaults from both aptitude and apt-get when i attempt update.

sudo aptitude update
Segmentation faultsts... 0%

I have an apt.conf file with

Apt::Cache-Limit 22582912;

This had been very effective with debian. Am I missing something? I'm running Edgy on a compac presario laptop with 521 MB memory (128M dedicated to graphics), a turion (AMD) 64 cpu.

Art Edwards

---

