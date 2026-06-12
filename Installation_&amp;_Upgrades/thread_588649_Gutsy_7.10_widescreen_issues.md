---
title: "Gutsy 7.10 widescreen issues"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by Slimo on 2007-10-23
I am having slightly different widescreen problems to others....or so it would seem.

I have upgraded (maybe..?) to Gutsy 7.10 and have a Samsung Syncmaster 931 widescreen LCD monitor and GeForce 6 series NVidia card.

Using the graphical Xorg config I can alter my resolution and set it to a nice looking 1440 x 900, which works most of the time.  Sometimes the resolution doesn't change and says all users must log off etc.  However, if the 1440 x 900 resolution works or not, whenever I log off and log on again, it is back to a 1280 x 1024 res or something....it doesn't seem to remember the settings.

Anyone else having similar problems?

---

### Post by jennymanda on 2007-10-23
You are amending the config file as root??

Also, why not just use the restricted driver app?

---

### Post by Slimo on 2007-10-23
I have been amending the config file (well, the screens and graphics file) as root.  It works at the time but not when I log out and log back in

What is the restricted driver app?

Thanks!

---

### Post by jennymanda on 2007-10-23
Sounds like you are not saving correctly - root will if you do it right,,, I reckon!

System > Admin > Restricted Drivers Manager

---

### Post by jennymanda on 2007-10-23
Or use this

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

and nvidia-settings as root

---

### Post by Slimo on 2007-10-23
Thanks for your help!

I have used the Restricted Drivers Manager to enable the nvidia drivers...will try changing resolution again as root.

If that doesn't work I will give Envy a try - thanks!

---

