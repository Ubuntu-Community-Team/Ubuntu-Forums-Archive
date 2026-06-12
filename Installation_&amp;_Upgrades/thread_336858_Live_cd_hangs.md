---
title: "Live cd hangs"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by Keajra on 2007-01-12
Hi,

Tried to run live standard cd version 6.10 Edgy Eft on my shuttle at home. The splash displays and the progress bar loads up and freezes at the end. I then see a thin single pixel wide green line of death spread across the middle of the screen and the application freezes. Any advice would love to run it!!

---

### Post by icefaerie on 2007-01-12
I am having a similar problem.  Here is a suggestion: when the Live CD boot screen loads asking you if you want to boot, check the CD for defects, etc., hit F6.  This will give you the boot options.  Delete the words "quiet" and "splash," and then hit enter.  The Live CD will now boot in verbose mode, so you can note where it gets stuck.

---

### Post by Keajra on 2007-01-12
Running it as you have described it tells me that it failed to start the x server (graphical interface). Looking further into this message I get ee no device detected and no screens found. Does this mean that it can't load the driver in a nutshell? I've loaded another Linux OS without difficultly last night built in 2001. So I'm thinking it can't be because the drivers are new?

---

### Post by ezsurfer on 2007-01-12
This certainly isn't new.  Seems many have this "hang".  Any fix in the making?  I easily loaded Mandrake ver 10, yet every version of Edgy I've tried to install to a laptop has frozen.  

I've tried X, K and standard flavor ubuntu.  

Went in and deleted the splash screens, removed acpi, video safe mode.  nothing seems to get it past the hang.

---

### Post by icefaerie on 2007-01-12
Keajra, do you know what graphics card you have?

---

### Post by Keajra on 2007-01-13
I certainly do, it's a RADEON X800 XT graphics card. Ubuntu Edgy did run on my HP laptop with xp pro just by the by. Would you recommend I try Mandrake, is it better than Ubuntu?

---

### Post by icefaerie on 2007-01-13
I wouldn't give up on Ubuntu just yet.  I would try downloading the alternate installer CD.  The installer is ncurses (text) based, but it is just as easy to follow as the Gnome GUI install.  This is just an installer, not a Live CD, but it seems you have tried Edgy on another computer.  So if you definitely want to install, go ahead and try the alternate CD.  Failing that, you might want to try a Dapper CD.  (I personally could not get the Edgy CDs to work and installed from a Dapper CD and then upgraded to Edgy.)

These threads might have some insights:

[http://www.ubuntuforums.org/showthread.php?t=190133](http://www.ubuntuforums.org/showthread.php?t=190133)
[http://ubuntuforums.org/showthread.php?t=294882&highlight=RADEON+X800+XT](http://ubuntuforums.org/showthread.php?t=294882&highlight=RADEON+X800+XT)

Good luck! :-D

---

