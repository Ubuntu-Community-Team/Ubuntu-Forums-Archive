---
title: "Can't set the right refresh rate of monitor on Ubuntu Studio"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by tungah on 2007-05-22
Hi everyone!
It's my first post here...
Well, I'm having some problem trying to set the refresh rate of my monitor on Ubuntu Studio.
I had the same problem on Feisty, but could fix by editing the  /etc/X11/xorg.conf and putting the right values of the vertical and horizontal rates.
But on Studio, I do that, and when i restart the X, and go on System/Preferences/Screen Resolution, the default rate is automatically set to 85hz, witch is the rate i what to use (before it was by default set to 65hz). But the screen continues flickering like it was still on 65hz... I don't know what to do... 
Please, if anyone can help me, I'd appreciate very much.

My monitor is a Samsung SyncMaster 997MB and my graphics card is a ATI RADEON 9600 PRO.

Thank you very much!

---

### Post by Bordy on 2007-05-23
You probably have a much nicer comp and monitor than I have (my laptop is a Thinkpad 600E!) but when I was getting terrible flickers on all distros I was trying to use (xubuntu, fluxbuntu, DSL, puppy, vectorlinux) eventually someone pointed me to changing my default depth from 24 to 16. Now, this will probably be different for your (most likely newer and better) computer, but its worth looking into I think.

hope that helped

---

### Post by tungah on 2007-05-23
Hey, thanks for that!
I'll check it out...

Thanks for your attention!

---

