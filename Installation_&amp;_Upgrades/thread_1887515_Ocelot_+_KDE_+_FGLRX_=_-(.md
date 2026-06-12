---
title: "Ocelot + KDE + FGLRX = :-("
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by maestrobwh1 on 2011-11-27
I am disappointed that after being able to get such combinations to work since Dapper 6.06, I ended up with some major issues that either I am now too old and impatient to iron out, or there were some major overlooks when dealing with amd/ati and the issues were insurmountable for the amount of time I was willing to put in being a seasoned veteran. 

First, since Lucid, I was never able to use jockey to install the proprietary driver.  Always borked.

Same deal with Ocelot.  Fails in the middle and I had to remove all the partially installed stuff.  The ATI installer ran and created fglrx.ko  Nice there, since I had issues with both Lucid and Natty with the standard kernel.

BUT it seemed overtly sluggish and garbage would appear during minimize and maximize.  I could not resume the screen from suspend.  One of two things would happen
1. Pitch black screen 
2. I had been thrown out of the desktop KDM restarted, so my suspended screen was gone, and on login, I would get 5 or 6 "Akondai blah blah pop ups"

One post suggested it works properly if compositing is disabled in Xorg.  That is not an acceptable workaround.  

I ended up re-imaging my Natty install back to the partition.  We just should not have to mess with such things at this point in Ubuntu's stage.  I did some searches, and didn't find anything much on how to fix it other than disabling composite.  Granted, it might have been a KDE/KDM issue as I did not try anything else with Ocelot.  

The open source radeon drivers, despite their advances still rely on the cpu rather than the gpu to create effects as noted by Xorg showing up in the top of the list when using the radeon drivers.

Using an ASUS 1201T notebook.  It generally has done pretty good with the 'buntus but not with this one.

If anyone has had luck installing the proprietary driver for ati with kde using jockey (hardware driver installer) while still having good performance and being able to properly resume from suspend, post back and I might consider giving it another try at some point.  I am kind of bummed, because I was looking to improved KDE performance, although I have the latest running on Natty but it seems a bit clunky and I am not happy that I upgraded to the latest KDE because it just slowed things down.

I should be doing fine with the hardware I have: AMD ati 3200 card, 4 GB RAM and 1.6 GHz Athlon Neo 64 bit processor.  Nothing unusual here.

---

