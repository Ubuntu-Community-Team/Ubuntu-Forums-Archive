---
title: "Upgrading to Dapper"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by jakedahn on 2006-03-13
Is there a way I can upgrade my current Breezy (5.10) to Dapper (6.04) with apt or without having to blow everything away?


I just don't want to get rid of everything I have, or go through the trouble of the bootloader, after a CD install.

BTW: I'm on a MacMini - so that means im on PPC instead of x86. Is there any known way of doing this?

---

### Post by oakz on 2006-03-13
I successfully upgraded by changing all "breezy"s to "dapper" in /etc/apt/sources.list. Then:

$ sudo apt-get update
$ sudo apt-get dist-upgrade

Others have had problems, so upgrade at your own risk :)

---

### Post by jakedahn on 2006-03-13
okie, here goes nothin!

---

### Post by rfruth on 2006-03-13
So howd it go jake ?

---

