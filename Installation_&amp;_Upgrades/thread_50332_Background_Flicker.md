---
title: "Background Flicker"
date: 2005-07-19
forum: Installation &amp; Upgrades
---

### Post by mcmuffy on 2005-07-19
Hi

I have done a fresh install of hoary and am having a few problems.
Basically there is a scanlines type effect on the desktop background. It only happens on the wallpaper not on the top and bottom menu bars or any windows that are open ,so running programs fullscreen is not a problem but its damn annoying when I am using the desktop.

I do not have this problem if I run at 1280x1024 60hz but the desktop looks wrong (does not fill the whole screen) as my monitors native is 1280x1024 75 hz. I have another hoary box hooked upto this monitor via a kvm which has no problems at 75 hz.

Monitor : Samsung Syncmaster 913N
Gfx Card : Nvidia 6800 GT 256MB
Memory : 1GB
CPU : Athlon 3200

This system also dual boots into Win XP (sorry but I have to play some games) which runs fine.

Sorry if this is hard to follow but its almost 4:30am and my brain is hurting  :???:

EDIT : I forgot, I do have the nvidia drivers loaded and get the nvidia logo on boot up.

---

### Post by WildTangent on 2005-07-20
it must be your graphics card drivers, or more likely, lack thereof. get the nvidia drivers from their site and install them. that should solve the issue

-Wild

---

### Post by mcmuffy on 2005-07-20
I have the drivers installed. The flickering lines are only a problem on the desktop area where the wallpaper is displayed, other than that everything works fine; even tuxracer works like a dream.

---

### Post by Joeb on 2005-07-20
[QUOTE=mcmuffy]I have the drivers installed. The flickering lines are only a problem on the desktop area where the wallpaper is displayed, other than that everything works fine; even tuxracer works like a dream.[/QUOTE]


Is it possible that you are telling it to display more colors at that resolution than the card/driver can produce at 75hz?  See if dropping the number of colors fixes the problem.

Joeb

---

