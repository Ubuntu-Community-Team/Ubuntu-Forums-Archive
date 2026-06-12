---
title: "&quot;over range&quot; install problems"
date: 2006-03-24
forum: Installation &amp; Upgrades
---

### Post by General Moskovich on 2006-03-24
I have a REALsync monitor that I'm pretty sure is only capable of running in 1280x1024 mode. I'm trying to install Breezy. When I press enter (to try the live CD during bootup) it starts to initialize the installation but stops and my monitory displays "over range". I've tried a few different boot settings such as linux video=ofonly but nothing seems to work. Anybody have an idea?

Thanks!

Mosko

---

### Post by General Moskovich on 2006-03-25
In case this helps anyone else I was able to install using the following option

linux debian-installer/framebuffer=false

---

