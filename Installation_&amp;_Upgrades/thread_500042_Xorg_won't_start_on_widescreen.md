---
title: "Xorg won't start on widescreen"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by pavpan on 2007-07-13
I was trying to install Feisty on a friend's computer. He just got one of the new behemoth screens (and a new computer too) that displays 1920x1200. Its freeking huge. Well, I put in the live cd and tried to install, but it gave an x server not wet up error. I checked disk integrity, and it was fine.

Finally, I got a alternate install cd, which gladly installed, and so I got a command line. But still no gui.

Its a new Dell computer. If its necessary, I could get the model of the computer and the screen, or any other components.

Any help?

Possible problems:
Its a giant screen
Its an ATi Card

What I tried (as root):
dpkg-reconfigure xserver-xorg
nano /etc/X11/xorg.conf (the settings were there, I did this to check)

I've tried running in 8,16,and 24 bit mode.

Still no luck. So, any ideas?

---

### Post by dgcarter on 2007-07-13
Have u tried installing ATi Graphics drivers?
Have a look here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Pumalite on 2007-07-13
You are going to have to get your Monitor Manual and with the settings obtained: reconfigure xorg file in the section 'Monitor'.

---

### Post by pavpan on 2007-07-13
I'll try. I'll be over at my friends house in a few days and have a go at it.

---

### Post by pavpan on 2007-07-15
YAY it works. Thanks so much guys! The resolution is still screwed up but I'll install ATI drivers and it should then be perfect. Once again, you guys are great, thanks for the help.

---

