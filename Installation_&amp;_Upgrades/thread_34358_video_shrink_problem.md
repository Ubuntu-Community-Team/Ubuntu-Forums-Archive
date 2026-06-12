---
title: "video shrink problem"
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by seti@tquadrado.com on 2005-05-14
Hi,

after installing new 5.04 Ubuntu (had 4.10), everything seems ok but the look in the laptop monitor. It is using VGA size, not the full screen.

I've done an automated "sudo dpkg-reconfigure xserver-xorg", but with default values everything is the same.

The preferable video mode is for 1024x768.
Where can i fix this ?

-- 
regards,
pedro mg

---

### Post by seti@tquadrado.com on 2005-05-14
Ok,

fixed.
Has to do with the /etc/X11/xorg.conf Monitor Section.
Had to add Modelines "1024x768" 85 1024...*

* these values vary from model to model. Try to Google it for your brand.

---

