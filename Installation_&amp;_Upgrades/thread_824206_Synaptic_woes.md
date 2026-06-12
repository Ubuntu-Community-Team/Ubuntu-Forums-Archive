---
title: "Synaptic woes"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by Wolfx25 on 2008-06-09
Hello all

Recently I reinstalled Ubuntu 8.04 onto my laptop. After updating, restarting, and then installing the restricted drivers for my wireless card I found myself unable to install any software using synaptic. Every time I try to install something, I get the error message "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report." When I run dpkg --configure -a, it says I need superuser privileges. I have no clue how to get these. 

However, if I start it without privileges, I don't get this error, not that it does my any good.

Wolfx25

---

### Post by Pumalite on 2008-06-09
sudo dpkg --configure -a

---

