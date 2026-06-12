---
title: "xorg.conf"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by Dragutin on 2007-10-23
Ok, sorry for the noob question: 

After upgrading to 7.10, my ibm t42 worked just fine.  Then restricted drivers manager told me it found a driver for my modem.  sweet! so i installed it, restarted, and my screen broke.  It only goes into 800x600, says it's a vesa card, etc.  just generally not too happy.  I backed up my xorg.conf then deleted it.  everything turned out happy! My screen is 1024x768, things work smoothly.  When I go to my xorg.conf file to edit my scroll wheel settings, however, xorg.conf isn't there! what?! I thought ubuntu would put in a default xorg.conf! 

I restored the xorg.conf backup i made, it broke the screen again.  I saw an xorg.conf.failsafe file in the /etc/X11 dir so I tried restoring that instead, screen still broken.  

How do I get it so that my screen stays in 1024x768 but also have an xorg.conf so i can have a scroll wheel?

thanks~

---

### Post by NilsE on 2007-10-23
With the bullet proof xorg it will not always create an xorg.conf so that is why it is missing.  However I think the following command will create one aftyer you answer a few questions.

sudo dpkg-reconfigure -phigh xserver-xorg

If it does not then try it without the -phigh (it limits the reconfigure to video)

---

### Post by Dragutin on 2007-10-23
thank you thank you!

xorg is there and res is still 1024x768

only thing is that in system>admin>screens and graphics
screen model is unknown and only options are 640x480 and 800x600 - dunno why this is but it doesn't seem to be making a difference.

---

### Post by NilsE on 2007-10-24
> **Dragutin said:**
> thank you thank you!

xorg is there and res is still 1024x768

only thing is that in system>admin>screens and graphics
screen model is unknown and only options are 640x480 and 800x600 - dunno why this is but it doesn't seem to be making a difference.
Glad it is working for you.

Screens and Graphics is new and  isn't quite up to date with all displays so you have to tinker some to find a model selection that works with your display. If you don't need dual monitors etc. don't even mess with it.  Just try screen resolutions under preferences.

---

