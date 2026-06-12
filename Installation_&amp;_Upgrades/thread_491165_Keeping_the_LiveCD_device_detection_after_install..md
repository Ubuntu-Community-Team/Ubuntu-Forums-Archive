---
title: "Keeping the LiveCD device detection after install."
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by arathorn2nd on 2007-07-03
Hello.

I just installed Ubuntu on a USB Hard Disk for recovery reasons, but I have a problem with hardware detection when using this on another computer, mainly the videocard for Xorg.

Is it possible to keep the LiveCD boot script that detects and configures these devices on a real installation like this?

Thanks,
Paulo.

---

### Post by matt_heys on 2008-03-26
I want to do this also, I know it's 9 months since your post but I'm a firm believer in using the search button.

The only posts I’ve found so far about auto configuring Xorg is to run "dpkg-reconfigure -phigh xserver-xorg" I added this to the boot scripts but on some systems I get a blue screen prompting for a screen resolution.

The LiveCD doesn't do this on the same systems so there must be something I am missing.

Currently I have deleted the xorg.conf entirely and rely on it finding the best way itself, so far it seems ok but I don't know if this is a good way of doing it, I doubt it somehow.

My next step is to compare all the rc*.d scripts from the LiveCD and from my USB install to see if there is something in there doing an automatic detect.


If anyone knows exactly how the LiveCD generates its xorg.conf then I would be very interested to know, most of the other hardware appears to go in without any problems.

---

### Post by matt_heys on 2008-03-26
Can anyone confirm if this would work.

adding somewhere in the boot sequence this :-

xdebconfigurator -i
dexconf

I noticed that the boot cd does not appear to use xdebconfigurator so I am still at a loss how it sets up the hardware.

---

