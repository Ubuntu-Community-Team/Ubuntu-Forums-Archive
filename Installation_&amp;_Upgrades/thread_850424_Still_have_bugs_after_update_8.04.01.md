---
title: "Still have bugs after update 8.04.01"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by arashiko28 on 2008-07-05
I am up to date and the lsb_release -a shows
> Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy


But still have the problem of not being able to configure anything else than the keyboard with
> sudo dpkg-reconfigure xserver-xorg

I need to change some RAM settings and to change my video settings. Not even going as root on recovery mode, I still get only access to change the keyboard. I want the list! The one with the devices and drivers!!!! ](*,)
I'm going mad with this, I have now 2 months trying to solve this...

---

### Post by avtolle on 2008-07-05
Try```
gksudo displayconfig-gtk
```for display help, and perhaps help with the graphics card.

---

### Post by arashiko28 on 2008-07-05
Pretty useful, but it's not what I need. I need the list where you change your driver for VESA and back, where you configure the amount of RAM shared with the video. That's exactly what I need.

---

