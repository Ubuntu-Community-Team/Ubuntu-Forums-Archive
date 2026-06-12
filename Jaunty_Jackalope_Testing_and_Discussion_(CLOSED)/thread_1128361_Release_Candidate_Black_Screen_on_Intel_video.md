---
title: "Release Candidate Black Screen on Intel video"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2009-04-17
Launchpad Bug #304871 is back.  Integrated Intel graphics i845 boots to black screen on CD Live and install on Ubuntu and Xubuntu.  

I had to boot CD Live, edit command line, remove quiet splash, add single to get recovery mode.  Then in root prompt nano /etc/X11/xorg.conf to add Option "NoAccel" just after "Configured Video Device".

Same thing on install.

Update Manager lists 49 updates already, NONE of them in xorg to fix this bug again.

Performance is sluggish on scroll etc to say the least.  

What happened?  It was fine on Beta?

Jerry

---

### Post by jerrylamos on 2009-04-17
Today's updates, April 17, did fix the problem for the installed Xubuntu. Will try Ubuntu next. There weren't any xorg updates but there was a kernel update.

The release candidate (as in Daily Build 20090414) boots to black screen unless I do "NoAccel".

Thanks, someone, hope the CD Live gets fixed too.

---

