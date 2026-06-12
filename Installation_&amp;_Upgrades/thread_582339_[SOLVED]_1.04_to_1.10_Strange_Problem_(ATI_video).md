---
title: "[SOLVED] 1.04 to 1.10 Strange Problem (ATI video)"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Brandito101 on 2007-10-19
Hi there,

I should start by telling you I'm fairly new to linux. I just upgraded from 1.04 to 1.10 via the update manager. Contents download and installation goes fine then my machine reboots to the OS boot selector and I choose the top most option (Ubuntu 1.10 kernel 2.6.22-14). Ubuntu loading screen comes up then it boots to a black screen. I then reboot and choose kernel 2.6.22-16. For some reason this kernal boots fine. I then go into Restricted Driver Manager and activate my Radeon 1900xtx and reboot. Now 2.6.22-16 also boots to a black screen except I can hear the the log in screen sounds. So, I just go ahead and type in my log in information and suddenly I'm staring at my gnome desktop (???). First off, why is kernel 2.6.22-14 not working (do I need to edit my xorg.conf)? And two, why is my screen black ONLY for the log in screen (w/ kernel -16)?

Thanks so much,
Brandon

---

### Post by Brandito101 on 2007-10-22
OK, go ahead and ignore this thread. I was able to log into kernel 2.6.22-14 by running

sudo dpkg-reconfigure xserver-xorg

and changing my video card drivers to vesa. I ended up fixing my log in screen and deleting my older kernels anyways.

---

