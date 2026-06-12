---
title: "Ran apt-get upgrade and now I cannot boot"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by jaden403 on 2008-07-08
I am currently running the latest release Ubuntu and ran apt-get to make sure everything was up-to-date.  I turned my machine off and came back to it a few days later.  The problem is that now I cannot boot.

I can get as far as the GUI trying to load, but then everything stops.  At first I thought that maybe it was my monitor, but I can boot into command mode.  Now I am thinking that maybe it is a problem with my video card.  I say this because it appears that my machine is booting, even though there is no display.  If I start hitting buttons I can hear the "drum-roll" through the speakers - the same sound you get when you enter an incorrect login password.  

So, my question is, is there a way to pinpoint exactly what the problem might be, if it is indeed a problem with the video card?  

Thanks.

---

### Post by upchucky on 2008-07-08
xorg.conf needs to be redone, the upgrade poooched it, you may be lucky and be able to get settings from the backed up xorg that upgrade made.

---

### Post by jaden403 on 2008-07-08
Thanks for the response. 

A few minutes ago I tried - on a whim - to simply type in my username and password, even though the screen was black.  The crazy thing is that it loaded the GUI fine and all is working well.  Of course, I know this is hardly a solution, but what exactly does this mean?  Does this relate to xorg.conf?

---

