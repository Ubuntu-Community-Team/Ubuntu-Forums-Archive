---
title: "Nvidia driver problems"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by coehorn on 2010-12-04
Just installed 10.04 on a previous windows machine that had been hit by a whopper of a virus.  I choose 10.04 over 10.10 because of problems I had on another machine with 10.10.

The video card is a Asus GT240 with 1 gig of ram.  It's driving a monitor via HDMI connection at 1920 × 1080.  When I install the Nvidia driver, the fonts for the KDE menus (and the Firefox browser menu .... File, edit, view, history, etc) are so tiny, I can't read  them.  Not even with a magnifying glass.  The monitor is 32" diagonal (Sony Bravia) so this is is majorily tiny.  So tiny that I can't understand what the font menus say.  I have to reload the OS from scratch.

The same thing occurred trying to install 11.3 Suse, so it's definitely a problem with the Nvidia proprietary driver.  What's the best method to resolve this?  My theory is that the hardware is uncommon enough that this bug with this card has not been discovered.  I'm thinking that rolling back to an earlier driver (at one attempt per system install) will not resolve this.

Ideas?  Should I contact Nvidia directly?  Mods, is this report in the correct place?

---

### Post by efflandt on 2010-12-04
That probably is not a video card thing and I do not think it happens with gnome (I was using GT 220, and now GT 430), so it may be the way that KDE makes assumptions about something.  Are you sure that you are using the native resolution of your display?

One thing that may throw it off is the screen size X tries to determine from EDID of the monitor or TV (or an old xorg.conf from different monitor).  For example X thinks my 32" 1080p HDTV is 52", but I only have one display connected and not a larger virtual desktop size, so it would have no reason to pay attention to that. I don't know if the indicated default 96 dpi in gnome reflects EDID screen size.  The 10 or 11 point fonts are sort of small if you are tired and blurry eyed.

But even if fonts are small, they are sharp, and it is easy enough to set larger fonts and/or higher dpi like 120 if you do not have good vision or proper eyewear.  Or there are Assistive Technologies for people who cannot see well.  Or if all else fails, you can set a lower screen resolution like 1360x768 or 1280x720.

---

### Post by coehorn on 2010-12-04
> **efflandt said:**
> That probably is not a video card thing and I do not think it happens with gnome (I was using GT 220, and now GT 430), so it may be the way that KDE makes assumptions about something.  Are you sure that you are using the native resolution of your display?

One thing that may throw it off is the screen size X tries to determine from EDID of the monitor or TV (or an old xorg.conf from different monitor).  For example X thinks my 32" 1080p HDTV is 52", but I only have one display connected and not a larger virtual desktop size, so it would have no reason to pay attention to that. I don't know if the indicated default 96 dpi in gnome reflects EDID screen size.  The 10 or 11 point fonts are sort of small if you are tired and blurry eyed.

But even if fonts are small, they are sharp, and it is easy enough to set larger fonts and/or higher dpi like 120 if you do not have good vision or proper eyewear.  Or there are Assistive Technologies for people who cannot see well.  Or if all else fails, you can set a lower screen resolution like 1360x768 or 1280x720.





The fact that two different distros both crash leaves me thinking that the driver is the problem.  

Now I'm fighting new demons.  I did a new install of 10.04 on a T61 Thinkpad tonight.  The install went perfect (speaking from over a decade of Linux experience) but when I went to activate the Nvidia proprietary drivers for an Nvidia Quadro NVS 140M vidcard, it crashes.  Totally crashes on boot.  WTF??  What is going on?  Has my diet had too much aluminum that I am going senile?

---

