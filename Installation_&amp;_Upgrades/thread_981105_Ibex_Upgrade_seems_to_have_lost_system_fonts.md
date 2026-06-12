---
title: "Ibex Upgrade seems to have lost system fonts"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by patrick.waring on 2008-11-13
I think it is easy to summarise my problem. There is no text in OOOrg menus. There is no text in KWrite sub-menus. You can still write a legible document in either. If I type in the document area of Abiword, the cursor moves but no permanent text appears. Abiword menus are fine. Evolution and Firefox are fine. If you look really closely when text fails to appear, you can see it for an instant about half the time. I fear similar problems could be found in other apps. This is all since my recent upgrade (not re-install) to Intrepid Ibex from Hardy. 

After reviewing the forums I have tried uninstalling and reinstalling with Synaptic, deleting the OOO hidden directory in home in between to force its re-creation, no change. Checking and unchecking the 'use system fonts box' in OOO (difficult when there is no text!) made no difference. I upgraded to OOO 3.0 No change. I set new fonts in System>Preferences>Appearance>Fonts. No change. sudo fc-cache -f -v had no effect. Installing lots of random extra fonts has not helped. Another weird thing - I can sometimes see the missing OOO menus in black correctly positioned on the wallpaper when I click the show desktop icon and then re-display the OOO writer window. They are there for about a quarter of a second and then get overwritten by the full window.

This looks like it should be a really simple system-wide fix if only these clues could tell a knowledgeable person where it should be applied!! I suppose downloading the iso, backing up and re-installing would fix it, but would rather not go through setting up users and emails if it could be avoided.

---

### Post by patrick.waring on 2008-11-13
FIXED (Sort of!) After having a cup of tea and a think I disabled the proprietary Nvidia driver for my GeForce 4 MX 440 video card. Problem has gone. Along with my Compiz effects....

[Edit] I applied this:- [http://www.nvnews.net/vbulletin/showthread.php?t=122695](http://www.nvnews.net/vbulletin/showthread.php?t=122695)

and OOO worked.

I added 'Option "RenderAccel" "0"' to the Device section of xorg.conf

from the end of this:- [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/251107)

and KWord and Abiword were fixed. Let's hope the nvidia driver works out of the box soon!

---

### Post by DavidW2 on 2008-11-14
I haven't tried Abiword or KWrite but I am running the proprietary Nvidia driver. And I am having trouble with the fonts on OOo.  The way to get them back was to turn off the visual effects under System > Preferences > Appearance > Visual Effects.

I need the proprietary driver to get the right screen size - 1280x854.  I haven't been able to get that size with the  nv driver.

[I wasn't able to use the Visual Effects with previous versions of the Nvidia driver so now that I can run them I really want them. I guess I'll have to keep playing around to find a better solution.]

---

