---
title: "changing locale"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by pesachzon on 2005-10-26
Hi, since I installed ubuntu 5.10 my locale changed from en_US to en_CA and things started crashing after printing this message:

Warning: locale not supported by C library, locale unchanged
Warning: locale not supported by Xlib, locale set to C
Warning: X locale modifiers not supported, using default

How can I change the system locale to en_US?

thanks

---

### Post by Xian on 2005-10-26
$ sudo dpkg-reconfigure locales

---

