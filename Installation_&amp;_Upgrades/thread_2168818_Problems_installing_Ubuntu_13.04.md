---
title: "Problems installing Ubuntu 13.04"
date: 2013-08-19
forum: Installation &amp; Upgrades
---

### Post by paglia96 on 2013-08-19
I'm trying to install Ubuntu 13.04 on my new notebook, a Toshiba c855-233, Initially I couldn't get further than the grub menu, now I have made a little step forward.


Adding 'nomodeset' to the boot option, I get to the Ubuntu splash screen, which seems to load (the dots are animated), but then the animation stops and I'm stuck on the splash screen.


The graphic card is an AMD Radeon HD 7610M.


Removing "quiet splash" from grub options (and keeping nomodeset) I get to this screen where it once again get stuck: [IMG]https://dl.dropboxusercontent.com/s/kg5u7mj4phspbjz/IMG_20130819_172427.jpg[/IMG]


Sorry for the low quality but opening it at full resolution it is readable. The [fail] is about "restore sound card(s) mixer state(s)"

---

### Post by ubfan1 on 2013-08-19
Try switching to a virtual terminal with crtl-alt-F2  (any fuction key 1-6).  Or just alt-F2, since the control is used when running X and you are not.  alt-F7 should be the login screen running X, try that.  You should able to login on a virt term and check the logs for errors, but it looks like a video problem.

---

### Post by paglia96 on 2013-08-19
Thaks for your response.

Accessing a virtual terminal doesn't work. I believe the problem is with the screen. If I connect an external VGA screen i can get to the desktop where I can only move the mouse and I can access the virtual terminal on the VGA screen. 

From there which command should I use?

---

### Post by paglia96 on 2013-08-19
Here is xorg log [https://www.dropbox.com/s/r314cmcwim9pwdo/0.txt](https://www.dropbox.com/s/r314cmcwim9pwdo/0.txt) Hope it's useful

---

### Post by ubfan1 on 2013-08-19
X is running, so try your function keys to select the display -- F4 or F5 (can't tell from the image).  Once you get the proprietary drivers in place, the display manager will offer you more setup options to allow display selection.

---

### Post by paglia96 on 2013-08-19
Thanks but nothing.... both with nodemon and without, anyway I tried Ubuntu 13.10 (19 august 2913 daily build) and it works!


I would prefer not using a in development version but it's ok, even if it's too instable in two months is going to be released.


Even WiFi works out of the box!


Anyway if someone knows a solution it would be better, so please post it if you have an answer.

---

