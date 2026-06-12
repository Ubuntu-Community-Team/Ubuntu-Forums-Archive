---
title: "Startup Disk Creator crashes"
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by Ani on 2013-10-19
I am trying to create a USB startup disk to install Ubuntu 13.10 64 bit edition from an ISO file.

I run "Startup Disk Creator". At the end when it is installing the bootloader it always crashes. I checked the ISO image files and they are OK.

I am running "Startup Disk Creator" on a 64 bit Ubuntu 13.10.

[ATTACH=CONFIG]247076[/ATTACH]

What should I do now?

---

### Post by atomstark on 2013-10-19
You can try to wait like one minute before inout your password (when asked to install bootloader). It worked for me. You can input your password when the LED of your USB key (if it has one) stopped blinking.

---

### Post by averos on 2013-10-19
I would check the MD5SUM on the ISO file and make sure it downloaded correctly.

I usually use this nifty little tool for creating installation USB. Works like a champ for me. 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Worp8d on 2013-11-28
I'm having this problem right now too. My ISO is fine, and gparted doesn't make it far enough to install the bootloader.

---

### Post by Worp8d on 2013-11-28
...but unetbootin works great! Thanks!

---

