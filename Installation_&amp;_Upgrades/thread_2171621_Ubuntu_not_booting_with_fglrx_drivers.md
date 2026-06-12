---
title: "Ubuntu not booting with fglrx drivers"
date: 2013-08-31
forum: Installation &amp; Upgrades
---

### Post by pwert00 on 2013-08-31
Hi all,

I have a problem with my installation of ubuntu.  When I do a clean install of Ubuntu 13.04 on my HP Pavilion g6-2235us computer, my installation works well except for the screen will flicker and the computer will run slowly.  In the past, I go to install the fglrx video drivers to remove the screen flickering, but I've found that when I install it the computer will no longer boot.  Instead, the computer will boot to a black screen with a blinking underscore.  I have, in recovery mode, removed fglrx with
```
sudo apt-get remove fglrx
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
```
and I don't know if my code is the best, but it removes the fglrx drivers and my computer runs again, except very slowly and with the flickering.  



Does anyone know how to find what my problem is with the fglrx drivers?  Or, are there other drivers that I can use?  How do I get them?

Thanks.

EDIT:
after typing:
```
lspci | grep VGA
```
I get:
```
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Trinity [Radeon HD 7520G]
```

---

