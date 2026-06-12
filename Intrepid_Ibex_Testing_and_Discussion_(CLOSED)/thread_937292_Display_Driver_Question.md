---
title: "Display Driver Question"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by [S]Duke on 2008-10-03
Okay, so I know that ATI has yet to update their driver to 7.4, but my question is, is there ANY usable driver with Ibex for ATI cards?

I have an ATI Radeon HD 2600 512MB, and when I first booted up (following install) I got a black screen after the splash image, and heard the sound the computer makes on getting to the login screen, but the screen stayed black.

The only way to get to the login at all was to edit xorg.conf to use "vesa" as the driver, but that gives me a horrible 800x600 resolution.

Is there anything usable or should I just reinstall Hardy?

Thanks =D

(Please don't mistake this as a complaint thread, I'm perfectly aware it's a beta release and bound to be imperfect, I'm just wondering if there's any way to use it)

---

### Post by bpl07 on 2008-10-03
I'm using the opensource ati driver for now.  This [wiki site]("https://help.ubuntu.com/community/RadeonDriver") should help you install and tweak it to your needs.

---

### Post by bpl07 on 2008-10-03
Sorry, I posted that a little too quickly.  Your card is an r600 model, so you should try the radeonhd driver if the normal ati doesn't work.  Here are a couple links which could be useful:

[http://www.phoronix.com/forums/showthread.php?t=9951](http://www.phoronix.com/forums/showthread.php?t=9951)
[http://dri.freedesktop.org/wiki/ATIRadeon](http://dri.freedesktop.org/wiki/ATIRadeon)
[http://wiki.x.org/wiki/radeonhd](http://wiki.x.org/wiki/radeonhd)

---

### Post by [S]Duke on 2008-10-03
Actually, my card was an ATI Radeon HD 2600, not a 2400 =P Not sure if your links still apply, but I followed the wiki and set up my xorg.conf and it seems to be working just fine, so yay =P (upon further playing with it, it seems Desktop Effects are broken, could it be because of your post above?)

---

### Post by psyke83 on 2008-10-03
> **'[S]Duke said:**
> Okay, so I know that ATI has yet to update their driver to 7.4, but my question is, is there ANY usable driver with Ibex for ATI cards?

I have an ATI Radeon HD 2400 512MB, and when I first booted up (following install) I got a black screen after the splash image, and heard the sound the computer makes on getting to the login screen, but the screen stayed black.

The only way to get to the login at all was to edit xorg.conf to use "vesa" as the driver, but that gives me a horrible 800x600 resolution.

Is there anything usable or should I just reinstall Hardy?

Thanks =D

(Please don't mistake this as a complaint thread, I'm perfectly aware it's a beta release and bound to be imperfect, I'm just wondering if there's any way to use it)

Delete your xorg configuration or else set the it back to the open-source driver. Reboot your computer, and when you get the black screen, switch to a virtual terminal and log in (e.g.: Ctrl+Alt+1).

When you're logged in, type the following:
```
$ DISPLAY=:0 metacity --replace
```

Switch back to your desktop (Ctrl+Alt+7). If you can see your desktop, then open Preferences/Appearances/Visual effects, and set it to "None".

---

### Post by bpl07 on 2008-10-03
double post

---

### Post by [S]Duke on 2008-10-03
> **psyke83 said:**
> Delete your xorg configuration or else set the it back to the open-source driver. Reboot your computer, and when you get the black screen, switch to a virtual terminal and log in (e.g.: Ctrl+Alt+1).

When you're logged in, type the following:
```
$ DISPLAY=:0 metacity --replace
```

Switch back to your desktop (Ctrl+Alt+7). If you can see your desktop, then open Preferences/Appearances/Visual effects, and set it to "None".
So then I assume the whole Desktop Effects thing won't be working until ATI releases their driver?

---

