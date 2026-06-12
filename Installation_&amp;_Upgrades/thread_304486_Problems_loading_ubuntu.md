---
title: "Problems loading ubuntu"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by liamhyland on 2006-11-21
My Ubuntu has failed to load for me.  I have been using it on my Sony PCG-FX140 laptop and dual booting.  I was trying to get my wireless working and then came problems.  Now when I turn on my computer it goes into booting up ubuntu and all goes well until it loads things, pauses and then I get a screent to say that 'failed to start the x server' and then a message 'would you like to view the detailed x server output as well'.  When I say yes I get lots of information starts with 'x window system version 7.0.0' and the last line reads:  '(==) Using config file: "/etc/X11/xorg.conf".  I have tried many starts but have no luck.  What can I do to get Ubuntu 6.06 back again.  Thanks, in anticipation.  Liam

---

### Post by ReaderRat on 2006-11-21
When you get to the "failed to start......" and a black screen,  hit CTRL+ALT+F1 to get into terminal and try this:
```
sudo dpkg-reconfigure xserver-xorg
```
to see if it gets you back on track.

---

### Post by liamhyland on 2006-11-21
Thank you Readerrat for your reply.  Too bad I do not get that dark screen but a blue one and then it askes me for the config system.  When I tried the dpkg-reconfigure xserver-xorg it gave me a challenge by asking me info about my Sony system that I took a gues s and ended up with the name of my laptop and a '#" sign.  I am not sure what I have to do now. Liam

---

