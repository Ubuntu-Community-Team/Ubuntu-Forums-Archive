---
title: "New graphics card - need help please"
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by Ben909 on 2006-12-20
Hi
This is my first post, so I apologise that it's for a request for help...
I'm a very novice Ubuntu user. That needs to be said right away, as my understanding of any replies might be limited!

I had a fully working installation of Ubuntu 6.06 on my PC (dual-booting with XP). Everything was going great until I got a new video card (Nvidia 8800 GTX). Now I'm no longer able to reach the pretty logon screen, and am instead presented with a textual logon prompt. 

Please can anyone advise me as to what command(s) I need to type to obtain and install an appropriate driver?  I'm sorry if this question is very basic, but as I said, my Linux knowledge is extremely limited at the moment.

Many thanks!

---

### Post by daspazz on 2006-12-21
Try logging in and then try to startx at the prompt to see if xwindows will start.

What happened is your old xconfig file is not set to handle your new card. 

I am new to ubuntu so I don't know the command to rerun the xconfiguation tool so you can repair the file.

But this happens in Linux when you make a radical change to your video subsystem and don't properly de-configure your video settings.  If you can get xwindows to manually start it may trigger the reconfig utility, but most likely you will need to manually "configX".

Can you boot off of the live CD?  That might let you get more information about the "new" setup.

---

### Post by christhemonkey on 2006-12-21
Try changing the video driver to "vesa":

First log into a terminal,

then reconfigure the X server:
```
sudo dpkg-reconfigure xserver-xorg 
```

And then choose vesa for the graphics driver.

---

