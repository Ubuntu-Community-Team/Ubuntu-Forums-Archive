---
title: "Help finishing up Lenovo U110 Install"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by dmunk on 2008-05-11
Hello,

I've been able to get Gutsy running on my Lenovo U110, except that I can't seem to get the graphics working entirely (or suspend, but I'm not worrying about that yet).

I was able to use the Live CD with 800x600 resolution.  I installed and updated everything and then ran

sudo dpkg-reconfigure -phigh xserver-xorg

which detected the Intel video card &#8211; it has the X3100.  xorg.conf looks fine to me, but I can't get anything higher than 800x600.  I took a detected modeline from the Xorg.0.log file for the desired 1366x768 resolution and put it into the xorg.conf file, but it didn't make any difference.

Any help would be really appreciated.

Thanks.

---

### Post by dmunk on 2008-05-11
Thanks for the thought, I'm starting from a clean install though...

---

### Post by dmunk on 2008-05-11
I've tried running with no xorg.conf and get the same result.  It looks like an output TV is getting detected, but I don't have anything display connected at all.

---

