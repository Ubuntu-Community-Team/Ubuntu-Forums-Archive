---
title: "Installing Ubuntu 7.10 on a desktop with Intel 915 video card"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2008-06-04
At the office, I had suggested to install Ubuntu on a desktop that no one uses but when I tried the live CD, the normal live-boot produced erratic graphic pattern all over the place. Booting in safe graphic (writting this thread in that mode), I can see that the video card on it is not found in the  available driver list (see below). 

Where can I find this Ubuntu driver to have a desktop using the video card, running a desktop in OpenGL with no special effects at all ?

**VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)**


p.s. : it has Intel 915 in the list but doesn't match the actual video card description above.

---

### Post by Rocket2DMn on 2008-06-04
Once you install the graphics should be ok, your card will use the "intel" driver (the "i810" and "i915" drivers are deprecated).  The LiveCD just has minimal support for graphics cards, but it has the driver for when you install.  Also, you should consider using Hardy if you can, there isn't much point in installing 7.10 then upgrading to Hardy.  Note that Hardy has a new version of X, but your card should be just fine, I haven't seen any complaints about intel cards.

---

### Post by Browser_ice on 2008-06-04
I am using 7.10 because that is the only CD I have at the moment.

I could always upgrade to 8.04 later during the night or something.

So you are saying that if I do the installation, the driver will be found. Ok, All that is left to do is convince my manager to install either ubuntu or Fedora.

Fedora is a somewhat standard here at IBM but there are Ubuntu projects to install compatible/working IBM day-to-day softwares. 

Thank you.

---

### Post by spamking2000 on 2008-08-19
Hey - Using Hardy on a friend's computer with the same Intel 82915G card... he has a widescreen monitor, but the only resolutions that come up are 1024x768, 800x600, and 640x480. Intel's site says that this card will do 2048x1536 at 85 Hz maximum resolution, and the widescreen monitor that it is hooked up to should do at least 1360x768... but I can't even seem to trick xorg.conf into going into that resolution... when going into System -> Preferences -> Screen resolution, I still only get the 3 lower resolution modes.

Any help would be appreciated!!

Thanks,
spamking2000

---

