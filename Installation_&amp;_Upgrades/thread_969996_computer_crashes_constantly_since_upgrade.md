---
title: "computer crashes constantly since upgrade"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by yankes1903 on 2008-11-03
Since I upgraded a few days ago, my laptop completely freezes and I can't do anything but shut it off using the power button.  Whenever it happens, the lights on the keyboard start going crazy and flashing (the scroll lock, caps lock and all those buttons).
I had absolutely no problems at all since I installed 8.04 back in May, it never crashed or even froze once. (vista did freeze all the time and this was brand new in May, that's why I switched)
Anyone else having a similar problem?  I've had other problems since upgrading to 8.10 (like any web-site I go to tells me to install Java 1.5 or higher but I check firefox and it's the right version!)  Anyway this only happened once or twice the first day but now it's constantly happening.
Any suggestions would be great! It was so hard getting everything I need for work to work on here and I don't want to have to completely reinstall.
Thanks!

---

### Post by jerrylamos on 2008-11-03
Might help if you could list what computer you have and what the video graphics is.

There's such a wide range of hardware out there it is hard for us to guess what you might have.

One fix that helps on some pc's that have Intel graphics is:

boot in rescue mode
at the selection menu
choose root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit 
resume normal boot

compiz is the code that plays fancy tricks with video to get animations and eye candy.  It is not needed for function.  It can be installed again if you want to.

Jerry

---

### Post by yankes1903 on 2008-11-04
Thanks, it is Intel 945GM.  I'll give that a try, but in case that doesn't work, I have a Dell Inspiron 1420, Intel Core 2 Duo processor, not sure what else you'd need to know so I'll see if removing compiz helps.
Thanks!

---

