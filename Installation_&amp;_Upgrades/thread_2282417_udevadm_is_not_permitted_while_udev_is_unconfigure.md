---
title: "udevadm is not permitted while udev is unconfigured"
date: 2015-06-14
forum: Installation &amp; Upgrades
---

### Post by chandradeep1981 on 2015-06-14
Hi, 
yesterday i started updating ubuntu 14.04. While installing packages pc hung. After waiting for considerable time i tried to shut down pc, but it would not shut. Hence, i removed battery while pc was on. After restarting i got this message "udevadm is not permitted while udev is unconfigured" on a black screen. Even recovery mode is also showing same message. Please help me. Thanks in advance.......

---

### Post by dino99 on 2015-06-14
Never abort an upgrading process, you always get such issue ;) Instead try to resolve it by opening an other session: ctrl+alt+F1>6
When you upgrade, dont do it blindly, use 'synaptic' to update/upgrade a few packages at once, and watch the installation dialog box to be aware of possible problem.
In your case , better to start a fresh install.

---

