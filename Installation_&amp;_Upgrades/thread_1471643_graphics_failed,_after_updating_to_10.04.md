---
title: "graphics failed, after updating to 10.04"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by javiercmh on 2010-05-03
Hi,
I've been using Ubuntu for a long time and, like most of you, I wanted to get immediatly. No problem.

I changed (stupid) in Appearance, the splash screen's resolution, because I don't like the 640x400 (I think) resolution. It was a big mistake...

Now I turn on the computer, and when Ubuntu loads, I only see a lot of colors in my screen, with something that I think is the Ubuntu logo repeated in both sides of the screen.
 
Is there any way to restablish the resolution of the computer, or to restore the initial configuration, from Ubuntu Live CD or from a command line? In command line case, How can I load Ubuntu in text-only mode?

Sorry for my English, if something isn't clear, tell me.

thanks.

---

### Post by quixote on 2010-05-04
(Your English is fine! :) )

There are instructions about everything to do with [Grub2 here]("https://help.ubuntu.com/community/Grub2#Splash%20Images%20&%20Theming").  The most relevant bit for you right now is perhaps this: > Changing Resolutions w/ Splash Images

If the user wishes to change the resolution of the GRUB 2 screen while using a splash image follow these steps:

   1. Set the desired resolution in /etc/default/grub
          * Change the value of GRUB_GFXMODE= (Example: GRUB_GFXMODE=800x600)
          * If unsure of what resolutions are available to GRUB 2 they can be displayed by typing vbeinfo in the GRUB 2 command line. The command line is accessed by typing "c" when the main GRUB 2 menu screen is displayed.

...

GRUB 2 looks for a resolution setting in /etc/default/grub. If uncommented, the resolution is determined by this line:

    * GRUB_GFXMODE=640x480
    * If no setting is found in /etc/default/grub, GRUB 2 uses the resolution established in /etc/grub.d/00_header, which is set at 640x480. 
 

So, at least to get started, the simplest thing might be to boot from a livecd, mount your usual boot drive.  Let's say it's put in /media/endless-uuid/.  Use gedit as root by typing in a terminal: ```
gksudo gedit /media/endless-uuid/etc/default/grub
```find the GRUB_GFXMODE line and change it back to the ugly low resolution that works.  Then go to town with fixing it the way you like it. :D

---

### Post by javiercmh on 2010-05-08
sorry for keep waiting. Thanks for the information. Right now I can't try what you found, because I'm a little bussy. I hope you understand. Anyway, I will tell you if it worked.

thanks again,
Javier.

---

### Post by quixote on 2010-05-08
No problem.  Good luck and I hope it works!

---

