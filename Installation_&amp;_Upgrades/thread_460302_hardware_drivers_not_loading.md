---
title: "hardware drivers not loading"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by vergil on 2007-05-31
ubuntu 7.04 installs successfully but fails to start up. after showing the ubuntu splash up screen it gives- loading hardware drivers   failed  message. works if i select recovery mode. any suggestions.

---

### Post by bulldog on 2007-05-31
Try in console ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
It may or may not help,but it's a start.

---

### Post by vergil on 2007-05-31
didn't work, thanks anyways. i'll describe my problem better so u guys can understand.
first it takes an unnaturally long time at the black screen with the ubuntu logo and the orange loading bar. after that it displays these messages on the screen-
files needed to boot   ok
setting preliminary keymap   ok
preparing restricted harware drivers   ok
setting basic networking   ok
setting kernel event m,anager   ok
loading hardware drivers                  failed
loading kernel modules   ( here it gives a unable to reset reboot flag, disabled by hardware message)
next it displays some more messages without any problems.
the first time i ran ubuntu it did some check and displayed a correctin made to filesystem message. now it runs ok but after an unnaturally long times.  will this- loading hardware drivers failed-message affect me. please help. i m new to linux.

---

