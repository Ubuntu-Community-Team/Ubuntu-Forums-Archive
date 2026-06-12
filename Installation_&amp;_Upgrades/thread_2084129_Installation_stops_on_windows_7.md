---
title: "Installation stops on windows 7"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by Win7OS on 2012-11-14
Hello, i am trying to download wubi on my windows 7 pc.
During the installation i get stuck on this screen.
[http://i50.tinypic.com/2hz1ocx.jpg](http://i50.tinypic.com/2hz1ocx.jpg)
anyone know a fix or what the problem is?

---

### Post by Win7OS on 2012-11-14
anyone ?

---

### Post by Win7OS on 2012-11-14
and i just get this screen when i try boot ubuntu.

[http://i50.tinypic.com/2rn8zkl.jpg](http://i50.tinypic.com/2rn8zkl.jpg)

---

### Post by critin on 2012-11-14
> Hello, i am trying to download wubi on my windows 7 pc.
During the installation i get stuck on this screen.

Why don't you boot it to the first screen and choose TRY - LIVE before you attempt to install.  Try it out and make sure everything works.  Which  version of ubuntu?  12.04?  It works, but 12.10 doesn't have a wubi working correctly yet.

---

### Post by Win7OS on 2012-11-14
> **critin said:**
> Why don't you boot it to the first screen and choose TRY - LIVE before you attempt to install.  Try it out and make sure everything works.  Which  version of ubuntu?  12.04?  It works, but 12.10 doesn't have a wubi working correctly yet.

yes i tried 12.10 is that why its not working?
if so ill try 12.04

---

### Post by critin on 2012-11-14
Try this wubi installer, it is almost failsafe.  It shows 12.10, so perhaps the issue is fixed in this installer.

[http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows)

---

### Post by bcbc on 2012-11-15
You need to use nomodeset because you probably have an radeon or nvidia gpu: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

So, select Ubuntu, immediately hold down the SHIFT key. then when grub's menu appears, hit 'e' to edit the first entry, and add nomodeset as described in that link. Then Ctrl+X to boot.

---

