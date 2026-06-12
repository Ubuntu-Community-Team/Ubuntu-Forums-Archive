---
title: "jaunty openchrome"
date: 2008-12-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sintacto on 2008-12-21
Just wondering if anyone is using the"openchrome" driver.
I have no luck with jaunty i usualy add it to /etc/X11/xorg.conf file instead of vesa but it dont seem to work for me in jaunty.
I must say that it looks prety good with vesa (45 fps glxgears)
so was just wondering if others are using openchrome with jaunty?

---

### Post by mariuz on 2008-12-22
> **sintacto said:**
> Just wondering if anyone is using the"openchrome" driver.
I have no luck with jaunty i usualy add it to /etc/X11/xorg.conf file instead of vesa but it dont seem to work for me in jaunty.
I must say that it looks prety good with vesa (45 fps glxgears)
so was just wondering if others are using openchrome with jaunty?

I have only installed it from svn and it works somehow better 600->700 fps in glgears on cloudbook 
I can play opengl games without flickering (the old ones)
[http://forum.netbookuser.com/viewtopic.php?id=836](http://forum.netbookuser.com/viewtopic.php?id=836)

chromium works good , freedoom , super/extreme tux racer:guitar:

update:be aware that with latest xorg breakage (upgrade) you will have issues if you try to compile it from source
i think it gave me an abi missmatch or something, but before that all was ok

---

### Post by sintacto on 2008-12-24
thanks I finaly got openchrome on jaunty
I also tried your xorg.conf settings and for the first time my monitor said out of range then turns off.
besides trying them one at a time do you have any suggestion on improving openchrome/xorg file combinations my fpm is around 50 with openchrome now Ive had it faster before not sure what to try next
thanks

---

### Post by ShirishAg75 on 2008-12-25
can somebody enlighten what "openchrome" driver is for? Which chipset?

---

### Post by caryb on 2008-12-25
> can somebody enlighten what "openchrome" driver is for? Which chipset?
+1


Cary

---

### Post by loell on 2008-12-25
its for VIA graphics chipsets, if i'm not mistaken.

---

### Post by sintacto on 2009-01-03
A free and Open Source video driver for the VIA/S3G UniChrome, UniChrome Pro and Chrome9 graphics chipsets.
(CLE266, KM400/KN400/KM400A/P4M800, CN400/PM800/PN800/PM880, K8M800, CN700/VM800/P4M800Pro, CX700, P4M890, K8M890, P4M900/VN896, VX800)

---

