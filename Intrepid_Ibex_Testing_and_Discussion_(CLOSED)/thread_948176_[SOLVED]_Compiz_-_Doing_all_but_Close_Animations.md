---
title: "[SOLVED] Compiz - Doing all but Close Animations?"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sam Lars on 2008-10-15
I just upgraded from Hardy to Intrepid.
I went to change some of my Compiz settings that got changed, and noticed something odd.  All of my open animations work as expected, as do the minimize or focus animations.  However, whenever I close something, it just disappears.  I tried changing the effect for it and changing the filter, but everything still ignores my Close effects.
Any ideas?

---

### Post by Jove on 2008-10-15
Try unchecking "Fade on Minimise/Open/Close" in Fading Windows (under "Effects")

---

### Post by philinux on 2008-10-15
> **Jove said:**
> Try unchecking "Fade on Minimise/Open/Close" in Fading Windows (under "Effects")

We didn't need to do this before. Very convoluted.

---

### Post by jerrylamos on 2008-10-15
Compiz does nothing at all on this IBM Thinkpad R31, 32 bit Intel Celeron, Intel graphics.  When compiz starts the Thinkpad stops.

Compiz hangs the Thinkpad on boot just as soon as Gnome should show the first desktop, launchpad bug 277344.  

The only way I can boot CD Live is to switch to command line while Gnome is initializing and do killall gdm, then apt-get remove compiz.  Same thing with install.  Beta would install - doesn't use compiz - then boot in rescue mode to command line, and do apt-get remove compiz.

I infer compiz is to do eye candy on the desktop - I switch between full screen internet, full screen Office, full screen Picasa graphics, ... so the eye candy doesn't come into play.  I would gather compiz does its magic by doing fancy tricks with the graphics hardware & drivers.  The rub is there are so many different graphics out there that what might work on one hangs another altogether.

What I need is a choice - those that want eye candy can get it, those like me that don't want it don't have to suffer the consequences - and I need the choice at boot before the first desktop even appears.

Jerry

---

### Post by Sam Lars on 2008-10-15
I don't even have the Fading plugin enabled.

---

### Post by Jove on 2008-10-15
Yep, I know. Just uncheck the box I mentioned, even although Fading Windows isn't enabled. Hey - it worked for me.

---

### Post by Sam Lars on 2008-10-15
Well it didn't change anything for me...

---

### Post by shane19174 on 2008-10-15
> I just upgraded from Hardy to Intrepid.
I went to change some of my Compiz settings that got changed, and noticed something odd. All of my open animations work as expected, as do the minimize or focus animations. However, whenever I close something, it just disappears. I tried changing the effect for it and changing the filter, but everything still ignores my Close effects.
Any ideas?

I had a very similar problem after upgrading. Only the open window animation worked for me. Someone here on the forum recommended that I click the little yellow brush icon below the various animation settings, which restores the default settings or "resets" them. After doing so, all animations now work perfectly. (I can't remember if I had to reboot/restart GDM.) Hope it works for you.

Shane

---

### Post by Sam Lars on 2008-10-15
Thanks a lot, that fixed it, even without a logout!  I was a bit afraid of wiping my settings, but it's fine now.

---

### Post by shane19174 on 2008-10-15
Glad to see that it worked for you. By the way, credit goes to dngpng, who made this clear to me in the first place ([http://ubuntuforums.org/showpost.php?p=5942445&postcount=34]("http://ubuntuforums.org/showpost.php?p=5942445&postcount=34")). The thread also has some other useful info about compiz that might be worth looking at.
Shane

---

### Post by Tanker Bob on 2008-10-24
Super, thanks! This just fixed the same for me.

---

