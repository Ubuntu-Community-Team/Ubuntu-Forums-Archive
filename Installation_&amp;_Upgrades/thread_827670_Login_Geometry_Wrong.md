---
title: "Login Geometry Wrong"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by smflorkey on 2008-06-13
The boot progress display is nice and crisp with a nice, round xubuntu logo.  Then it switches to the login screen and the logo gets a little oval and the lines are not so crisp any more.  After I log in it goes back to native resolution for this LCD panel, 1280x1024, and the circles are round again.  What do I have to do to clean up the login screen (gdm?)?

TIA, 
Steve

---

### Post by dstew on 2008-06-13
In the /etc/X11/xorg.conf file, there is a list of modes in the Display subsection. The login sceen I think uses whatever is first in that list as its resolution. If you edit the file, and switch the first mode for one of the others, you might get a better login screen.

If you have ATI drivers, you might be able to do the same thing with the aticonfig program. I am not sure it works for Xubuntu though. See [this thread]("http://ubuntuforums.org/showthread.php?t=359310").

---

### Post by smflorkey on 2008-06-15
Thanks for the link to that other thread; I had not found that one yet.  My card is an old ATI Radeon 7000 -- too old for the current, fancy ATI drivers that include aticonfig.  I tried installing fglrx, but it did not run on this old card. 

My Section "Screen" did not have SubSection "Display" so I added it with the default depth and only 1280x1024 on the Modes line, but that did not change the login display geometry.  Still, it was a good thought, well worth trying. 
-- 
xubuntu 8.04 Sempron 2800+ 256MB RAM 80GB /dev/sda

---

