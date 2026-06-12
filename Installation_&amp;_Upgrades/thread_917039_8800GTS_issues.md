---
title: "8800GTS issues"
date: 2008-09-11
forum: Installation &amp; Upgrades
---

### Post by screwballl on 2008-09-11
Basics:
took ATI X1950GT out and put in 8800GTS
Ubnutu with Gnome and KDE 4.1 (default is KDE)

I recently (earlier today) took out my ATI X1950GT from my system which was working fine and displayed Compiz effects without a problem. Then I put in my newer evga 8800GTS 320MB and when it tried to boot, it just showed a black screen although I could see disk activity. So since this is dual boot, I booted into windows, removed ATI software and installed nvidia drivers without a problem.
Then back to Linux... this time when it booted it said booting in low resolution mode... so I repaired the Xserver and changed the driver to "nv".. it displayed the login prompt and after logging in, it went right back to the blank screen, even though it displayed disk activity.
I hard rebooted/reset again and same low resolution message again so I chose "vesa"... and once I got the login prompt I chose to use the Session Type of Gnome...
I got the desktop which worked fine, so I went into synaptic and installed the nvidia-glx-new (whatever it is called) and then rebooted the system... this time it came up to the login prompt, I changed the session back to KDE (4.1) and the desktop loaded but there are all sorts of graphical glitches... squares around buttons, compiz effects going crazy... so I tried removing compiz and the same thing is happening even after removing it. One major thing is that there are no glitches or problems when booting into Gnome...


Also, when I choose to Lock Screen or Logout, rather than go to the proper black screen or login page, I get a multicolored CGA type of display (see screenshot below)... I will also try to get a screenshot of some of the graphical glitches later today when I get a chance.

So what may be causing this? or is it simply that this is such a new video card (2006) that it is not supported properly in linux yet?

[IMG]http://img.photobucket.com/albums/v280/Screwballl/Computer/screenshots/DSCF0002.jpg[/IMG]

---

### Post by nerdzero on 2008-09-11
I have the same model card (different manufacturer) in my dual boot system and it works fine.  But I use Gnome and as you mentioned you are not having problems in Gnome either.  I don't get the funky colors on logout or when locking the screen though.

How did you repair the X server the first time you booted into lo-res mode?

---

