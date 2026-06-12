---
title: "gnome: failed to initialize HAL"
date: 2005-09-07
forum: Installation &amp; Upgrades
---

### Post by nosmij on 2005-09-07
After configuration on first boot into the desktop, gnome shows loading sessions, windowmanager etc but just when it drops into the desktop, it pops an error saying 

failed to initialize HAL

this is followed by nautilus, gnome-panel crashing. If you close the error msgs or click on 'restart app' this same problem contimues.

Initially I had problems with the xorg.conf mistakenly taking the mouse as /dev/input/mice..... and giving a fatal error, then it used to quit and attempt again in a endless cyle. I managed to drop into another shell just after the xorg was set up and changed it to /dev/psaux which atleast started the X server but then gnome hung on me.

What could be going wrong? And how can I rectify it? What is this Hardware Abstraction Layer doing and why is it there? 

I also have slackware 10.1 installed, but haven't come across anything called HAL so far.

I am using 5.04 with the default kernel.

Thanks.

---

### Post by amohanty on 2005-09-07
Some links that could possibly help you fix the problem:

[http://ubuntuforums.org/archive/index.php/t-23291.html](http://ubuntuforums.org/archive/index.php/t-23291.html)
[http://ubuntuforums.org/showthread.php?t=21887&page=1](http://ubuntuforums.org/showthread.php?t=21887&page=1)

HTH
AM

---

