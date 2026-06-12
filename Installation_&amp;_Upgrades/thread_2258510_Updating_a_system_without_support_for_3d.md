---
title: "Updating a system without support for 3d"
date: 2014-12-28
forum: Installation &amp; Upgrades
---

### Post by Camilia on 2014-12-28
When I tried to upgrade from 12.01 to 14.04 given link to thread on Updating a system without support for 3d. Instructions were to install the gnome-session-fallback package, and then on the login screen click the gear icon and select "Ubuntu-classic (no effects)". 

I was able to install the gnome-session-fallback package. Can't find option Ubuntu-classic (no effects). I assume they are talking about the gear on the right corner of the screen. Could it be somewhere else?

---

### Post by MAFoElffen on 2014-12-28
Support for the unity-2d package ended and is not available for 14.04 on... That Classic Fallback is the 2D choice. Sorry.

Reasoning was to Focus on Unity 8...

---

### Post by grahammechanical on 2014-12-28
You are at the login screen. Correct. Look at the panel where we put the password. There should be an icon above the panel and to the right. It is part of the overlay that creates the password panel. It will be the Ubuntu icon. Not the gear/cog icon.

When the upgrade to 14.04.1 is completed you will get, I guess, three login session options.

1) Ubuntu. This will run Ubuntu using llvmpipe. It is an open source video driver that is used as a fall back video driver for graphic adapters that cannot run Ubuntu Unity 3D. It gives an approximation of Unity 3D. You may find that usable considering the limitations of the hardware.
2) Gnome Flashback (Compiz)
3) Gnome Flashback (Metacity)

Gnome Flashback is the replacement for Gnome Fallback. One session will run on Compiz as the window compositor and the other will run on Metacity as the compositor. See which one gives you the best results. Both sessions have the old menu system and not Unity.

I would suggest that before doing the upgrade you activate the open source video driver instead of any proprietary video driver. Otherwise, the upgrade will bring in the latest proprietary video drivers and at this stage we do not know if these newer drivers still support your video card.

Regards.

---

### Post by Camilia on 2014-12-28
> **grahammechanical said:**
> You are at the login screen. Correct. Look at the panel where we put the password. There should be an icon above the panel and to the right. It is part of the overlay that creates the password panel. It will be the Ubuntu icon. Not the gear/cog icon.

When the upgrade to 14.04.1 is completed you will get, I guess, three login session options.

I am confused by your reply. 
1. I don't have an area to put my password. 
2. I have the latest open source video in synaptic manager
3. When I attempt to upgrade to 14.04 I get this -
Running the 'unity' desktop environment is not fully supported by your graphics hardware. You will maybe end up in a very slow environment after the upgrade. Our advice is to keep the LTS version for now. For more information see [https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D](https://wiki.ubuntu.com/X/Bugs/UpdateManagerWarningForUnity3D)

---

### Post by Camilia on 2015-02-03
I reinstalled ubuntu 12.04 via a flashdrive. Then attempted to upgrade to 14.04. Success. Thanks everyone!!. 

There are a few things like better about 12.04. Thus may go back to it.

---

