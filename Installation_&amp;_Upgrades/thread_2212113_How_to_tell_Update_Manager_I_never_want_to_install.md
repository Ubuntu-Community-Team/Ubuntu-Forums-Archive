---
title: "How to tell Update Manager I never want to install certain updates?"
date: 2014-03-19
forum: Installation &amp; Upgrades
---

### Post by Riothamus on 2014-03-19
Update Manager keeps  wanting to install these recommended updates:

fglrx - Video driver for the AMD graphic accelerators
fglrx-amdcccle - Catalyst Control Center for the AMD graphic accelerators
fglrx-dev - Video driver for the AMD graphics accelerators (devel files)

Every time it does this, my graphics card stops working, and I have to follow these steps to get it working again:
[http://askubuntu.com/questions/129597/how-do-i-fix-my-installation-of-ati-catalyst-video-driver-in-12-04-lts/218894#218894](http://askubuntu.com/questions/129597/how-do-i-fix-my-installation-of-ati-catalyst-video-driver-in-12-04-lts/218894#218894)

Is there a way to tell Update Manager I just don't want to install these updates ever? It's not a huge deal, but it's just getting annoying having to find those three packages and uncheck them every time updates are installed.

Thanks in advance.

---

### Post by slickymaster on 2014-03-19
The ubuntu documentation [has a page dedicated to this]("https://help.ubuntu.com/community/PinningHowto#Introduction%20to%20Holding%20Packages"), that will tell you how to hold a package, but with synaptics or the command line, and how to "un-hold" it

---

### Post by grahammechanical on 2014-03-19
Depending on the version of Ubuntu that we are using (which you do not tell us) we can go into Software and Updates and un-tick the box to update proprietary software. This should stop the proprietary video driver from being updated.

Again, depending on the version of Ubuntu, Update Manager should give us the option to un-tick packages that are to be updated.

Regards.

---

### Post by Riothamus on 2014-03-19
Thanks, unchecking proprietary software seems to have worked. Thanks to both of you for the help. I'll try and remember to post what version I'm using next time.

---

