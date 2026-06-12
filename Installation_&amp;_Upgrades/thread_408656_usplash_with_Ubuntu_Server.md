---
title: "usplash with Ubuntu Server?"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by navilon on 2007-04-13
I am using Ubuntu Server 6.10. It does not use a splash screen by default.

Is it possible to install it or do i need to switch to a different kernel?

---

### Post by tgm4883 on 2007-04-13
I suppose you could try "sudo apt-get install usplash" although im not sure what dependencies would need installing or if it would even run on the server kernel.

---

### Post by navilon on 2007-04-13
Sorry, I should of mentioned before. I've already installed usplash, it just doesnt seem to be showing up during boot

---

### Post by daniel of sarnia on 2007-04-13
It has nothing to do with your kernel, you need to either install the usplash-theme-ubuntu package, or it could be a setting in your bios that you may or may not be able to change. My D500 laptop won't show the splash either. Not since dapper, I don't know why.

---

