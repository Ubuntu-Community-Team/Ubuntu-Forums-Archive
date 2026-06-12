---
title: "Oh Deary me...."
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by Jasper73 on 2008-04-04
Hello
I have just fired up my notebook today and ran up Ubuntu 7.10 logged in correctly and ran a few updates (well 105meg worth) rebooted and now the beast just sits at a console prompt.  I can log in correctly using username and password however if i try and startx it fails can anyone help me out as to where to start looking please?

Cheers
J

---

### Post by Wobedraggled on 2008-04-04
paste the /var/log/Xorg.log file here, and we can see what the issue is.

---

### Post by Jasper73 on 2008-04-04
I have attached the file

---

### Post by Pumalite on 2008-04-04
You might want to try this:
sudo dpkg-reconfigure xserver-xorg

---

