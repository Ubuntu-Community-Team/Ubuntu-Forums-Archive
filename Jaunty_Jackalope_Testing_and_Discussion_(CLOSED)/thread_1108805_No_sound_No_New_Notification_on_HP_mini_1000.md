---
title: "No sound No New Notification on HP mini 1000"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bigbrovar on 2009-03-28
I just installed jaunty Netbook Remix on my hp mini 1000. am pretty much impressed with the looks and how snappy it is. the only problem am having with it is sound. i have never had a sound problem before hence i dont even know where to start trouble shooting. funny enough sound worked when i tried eeebuntu 1.0 which is based on hardy heron. also i noticed that the jaunty netbook edition doesnt come with the new notification system since the the desktop version. can any confirm if this is the way it was designed or a bug..

---

### Post by otchster on 2009-03-28
I too installed Jaunty on my HP Mini 1000 - it works great except for I have no sound!

The netbook acts like it has sound, even the key board hot keys mute and volume up and down correctly.

When I click Test in the sound settings, I hear nothing.  :(

---

### Post by FnMag on 2009-03-29
I am having the same problem...

i have tried several things including:
Checking to see if "audigy/analog" is checked.
getting the alsa driver and installing it. 
tried reinstalling
switched to the non-remix version.

It's getting really frustrating to say the least. I am a brand new Linux user, I really, really like it, but not getting any sound is ruining it for me..

  ANy help would be appreciated !

---

### Post by bigbrovar on 2009-03-29
This is obviously a regression as the sound works on hardy and intrepid. i would find time to file a bug about this.. 
@FnMag since you are a new to linux, i would suggest you try the latest stable version of ubuntu which is right now happens to be Intrepid Ibex (ubuntu 8.10) i run it on my mini and it detects everything out of the box. Jaunty is still at beta and although its stable ( works like a charm on my laptop) its still to recommended for new users because things might still break.

---

### Post by FnMag on 2009-03-29
Thats what i'd like to do, but am having problems with the mini 1000 recognizing the flash drive at start-up... But this isn't the place for that.

---

### Post by bigbrovar on 2009-03-30
have you considered trying the hp mie interface .. its possible to download the image and install it on ur hp mini ... although u will not be able to dualboot windows. and it would completely ease your drive and install the Mobile Internet Experience. I tried this an di found it to be a better experience .. right now my system starts faster and is more responsive. wireless,audo,skype,hibernation and suspense all work out of the box. plus the mie interface which is a beauty to behold .. u might want to try it out

---

### Post by oxboood on 2009-04-18
> **bigbrovar said:**
> have you considered trying the hp mie interface .. its possible to download the image and install it on ur hp mini ... although u will not be able to dualboot windows. and it would completely ease your drive and install the Mobile Internet Experience. I tried this an di found it to be a better experience .. right now my system starts faster and is more responsive. wireless,audo,skype,hibernation and suspense all work out of the box. plus the mie interface which is a beauty to behold .. u might want to try it out

Yeah but the shell/terminal is disbaled

---

### Post by sammcj on 2009-04-19
Hi,

I have a HP mini 1004TU.

Sound was working on 8.10, did an upgrade to 9.04 and sound is no longer working.

Flatmate has the same laptop with 8.10 and sound works fine.

I'll look into this, its probably just a modprobe or something with alsa mixer etc... :)

Sam.

---

### Post by crimsun on 2009-04-19
No, it's not just a mixer setting. There have been regressions in the jack event handling in 1.0.18. These are largely fixed for the HP Minis in 1.0.19. Karmic has these fixes.

---

