---
title: "Usplash low res"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by timzak on 2009-04-19
On my main system with a widescreen monitor, usplash looks horrible by default.  I installed startup-manager and it told me it was set to 640x480 8bpp.  I had the option of setting to a higher res and color depth, but no widescreen settings are supported so it looks stretched out.  Will this be addressed before Jaunty is released?

Interesting, on another system I have Jaunty installed, which uses a standard 4:3 monitor, it appears that usplash defaulted to a higher res and color depth.

My point:  Jaunty looks stunning in every other area, from login screen to desktop, but the first thing the user sees is Usplash, which looks terrible in comparison at 256 colors and 640x480.  I think for the other improvements to have more impact, this should be addressed asap.

---

### Post by antiram on 2009-04-19
edit /etc/usplash.conf with right resolution and execute update-initramfs

---

### Post by timzak on 2009-04-19
> **antiram said:**
> edit /etc/usplash.conf with right resolution and execute update-initramfs

Appreciate the workaround.  Thanks!

Does Canonical plan on fixing this?  Seems like a bad plan to make it look ugly by default and require user intervention to make it look as good as the rest of the OS.

---

### Post by macroshaft on 2009-04-19
Agreed, I have made similar comments to difficult areas of the system in the past and been met with an attitude wish suggests 'How dare you not have a degree in rocket science!'

It seems to me windows, as hateful as it can be, does cope remarkably well with the huge variety of hardware. Linux however does have a nasty habit of saying 'There, that's almost set correctly, now edit the config files yourself.'

It's not exactly mass market ready, however when was the last time linux asked you for the drivers to 'usb device' while you sit there screaming at the screen because you have no idea what drivers to get? Wins my vote every time!

---

### Post by timzak on 2009-04-19
Okay, my monitor's res is 1440x900 so I tried that and got the usplash screen in the right proportions, but off center.  After playing a bit, I settled on 1024x640, which is in proportion and perfectly centered, if a bit smallish.  I tried 1280x800 and that was also off center.  Weird.

---

### Post by MacUntu on 2009-04-19
Usplash tries to get the values for /etc/usplash.conf from the hardware but if the hardware doesn't report it correctly it might be wrong.

Usplash is far from being perfect but it is on its way out so I wouldn't expect the devs to put any more effort into this.

I only found it funny that they started to work on it for the last cycle (maybe!) it will be used. The problems were there from the beginning.


> It seems to me windows, as hateful as it can be, does cope remarkably well with the huge variety of hardware.

Hardware vendors develop with Windows in mind, Microsoft develops with nothing in mind, Linux develops with standards in mind.

---

### Post by macroshaft on 2009-04-19
I am aware that the problems we face (graphics are a perfect example) are solved in windows by collaboration between microsoft and the hardware manufacturers. I sympathise with how much harder the job is for the rest of the programmers having to go it alone so to speak but unfortunately the end user will not and it does give microsoft the edge.

However as I said before I'll happily give up my bells and whistles for a system that does as I say, rather then telling me what I want to do!

---

