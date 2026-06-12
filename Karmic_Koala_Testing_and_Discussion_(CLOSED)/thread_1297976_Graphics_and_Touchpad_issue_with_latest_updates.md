---
title: "Graphics and Touchpad issue with latest updates"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by winding.roadie on 2009-10-22
I'm running a Lenovo 3000 N100 laptop, with a built-in Intel graphics card, and have been running Ubuntu very smoothly on it ever since 8.04.  Normally, I would upgrade to the beta release, and have never had any problems doing so.  The same is true of 9.10, I never had any problems with the beta until yesterday.

I installed the automatic updates through Update Manager, and rebooted when prompted to do so.  The first issue I noticed was that my custom login screen no longer loaded (it had previously with the beta).

I've got two accounts set up on my laptop: my admin (sudo) account that I use all the time (and has Compiz running smoothly, could be important later), and a non-admin account without Compiz that I use for doing presentations.  When logging into either account, I noticed that the touchpad for my laptop was disabled.  Fortunately, a USB mouse was able to workaround this issue, although I would eventually like my touchpad back :frown:

The big problem I'm trying to figure out is that in logging into my admin account, I'm simply presented with a white screen (which I believe is my background color, behind my desktop image).  Nothing appears when I do anything, although I know things are open as I can access the right click and power menus to perform tasks.:confused:

Any ideas as to what might have caused this/how to fix it?  I'm pretty much stumped at this point, and have resorted to using my non-admin account for internet access.  Any help would be greatly appreciated.

---

### Post by winding.roadie on 2009-10-22
Well, booting into Failsafe GNOME seemed to fix the graphics problem, but not the touchpad.

Running an update-manager -d right now, with is giving me a partial upgrade.  I'll see what this does for me.

---

### Post by Mark Phelps on 2009-10-22
When you said you installed the latest updates, were these for 8.04? Or did you upgrade to the 9.10 beta?

When you did the Failsage GNOME, did it revise your xorg.conf? 

I'm asking because I'm running a Fujitsu tablet on 8.04 and had to do a LOT of customization to the xorg.conf -- which is why I have a copy squirreled away in case the working version gets clobbered in some way.

---

### Post by winding.roadie on 2009-10-22
Latest updates for 9.10 beta.

Haven't looked at my xorg.conf yet.  I might try that later.

---

### Post by Mark Phelps on 2009-10-22
> **winding.roadie said:**
> Latest updates for 9.10 beta.

Haven't looked at my xorg.conf yet.  I might try that later.

That probably won't help much because most of the touchpad/tablet/stylus stuff that USED to be configured in the xorg.conf file was moved out of there into FDI files (for 8.10 & 9.04) and something quite different for 9.10.

Sorry, don't know enough details about 9.10 to help you there.

---

