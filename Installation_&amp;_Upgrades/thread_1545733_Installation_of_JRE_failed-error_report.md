---
title: "Installation of JRE failed-error report"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by venkatana on 2010-08-04
I tried to install JRE 6 
After adding partner repository I wanted the updates by this command 
sudo apt-get update
I got the following error
E: Malformed line 54 in source list etc/apt/source.list (dist parse)

what does it mean and how to rectify.

---

### Post by dino99 on 2010-08-04
clean the sources:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

---

