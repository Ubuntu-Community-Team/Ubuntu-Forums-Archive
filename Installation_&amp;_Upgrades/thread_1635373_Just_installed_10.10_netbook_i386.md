---
title: "Just installed 10.10 netbook i386"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by jjmelo1 on 2010-12-01
Everything seems to have been installed correctly, but after I rebooted and inserted my PW the computer screen goes to a purple background, no desktop. Also, I did a full install, ubuntu is the only OS on my Toshiba Satellite A215-S7407.    Any help is much appreciated. 

Thank you

---

### Post by AbeJarano on 2010-12-02
Sounds like the display manager died.  It's X and gdm.  So from your purple screen try Ctrl-Alt-F1, log in, do 'sudo service gdm stop', do 'sudo delete /etc/X11/xorg.conf', then 'sudo service gdm start'.  Hopefully you'll get a lowres windowed display. Then find out what video chip and google see.  Maybe you'll  want to install the manufacturer proprietary driver.

---

