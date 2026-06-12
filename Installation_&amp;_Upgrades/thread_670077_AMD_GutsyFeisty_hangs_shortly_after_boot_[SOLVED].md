---
title: "AMD Gutsy/Feisty hangs shortly after boot [SOLVED]"
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by immesys on 2008-01-17
I'm posting this mostly to see if anyone else has had the same problem. It'll get into Gnome/KDE alright, on both the LiveCD and the installation but hang after a random period of time. I have an AMD 3400+ (

Somehow I found out that the problem was with CPU throttling, if you 'chmod 000 /etc/init.d/powernowd*' it fixes the problem. (This involves making it boot in single-user mode, chmodding powernowd, then initting runlevel 5)

This started with Edgy and is still around in Gutsy so I thought I'd post it here and see if anyone else had this problem.

---

