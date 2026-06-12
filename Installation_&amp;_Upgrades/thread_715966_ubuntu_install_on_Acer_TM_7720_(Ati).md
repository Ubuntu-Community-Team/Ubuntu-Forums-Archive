---
title: "ubuntu install on Acer TM 7720 (Ati)?"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by dennisros on 2008-03-05
Hi, I'm always having problems with installing Ubuntu on my Laptop Acer TravelMate 7720. The problem is always the x-org configuration and I cant get it to work. 
Can't load ubuntu because of this, then I found this site 
[http://wiki.x.org/wiki/radeonhd](http://wiki.x.org/wiki/radeonhd)
but I don't understand how to do it, I have the graphics card ATI Radeon HD 2600 and want the x-org to work with that, how should I do when I start Ubuntu and I ens up in terminal mode because unable to log in?
/Dennis

---

### Post by dstew on 2008-03-05
First you need to get a basic GUI desktop working. To do that, boot to a command line using recovery mode, enter```
sudo dpkg-reconfigure xserver-xorg
```That takes you through a text-based reconfiguration program. When you get to the part about the display, choose the vesa driver, and a lowish resolution, like 1024 x 768. After you have reconfigured, enter startx and the display should start. Once you have your desktop, look at the Restricted Drivers Manager in System --> Administration. Hopefully it will identify your card and let you install a driver for it.

---

### Post by dennisros on 2008-03-05
Thanks for the help, I will try.

---

