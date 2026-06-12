---
title: "UPS Recommendations?"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by nuubunster on 2006-09-21
Anyone know of good UPS systems for a desktop/web server environment?

---

### Post by wpshooter on 2006-09-21
As far a brand goes, APC.

However, if you are wanting to get the shutdown process to be automated thru the UPS vendor's own provided software on a Ubuntu/Linux system, all I can say is good luck or I hope you have someone available to you that is pretty much a Linux guru.

---

### Post by sal on 2006-09-21
if you go with apc there is an application in the repos called apcupsd that handles auomated shutdowns and all that stuff. it's command line only though,just to let you know.

---

### Post by tagra123 on 2006-09-21
There is also a progrm called nut -- I used it and it works fine with APC products

---

### Post by wkulecz on 2006-09-21
If you are talking APC units that are priced for individuals and sold at Fry's, Best Buy etc.  I can't recommend them.  They appear to work fine initially but then end up letting you down when you need it most becasue the battery is effectively dead but the UPS didn't detect it, so when the power goes out the UPS drops before the system has had a chance to shutdow -- the typical 2 minute default to shutdown ends up being 100X longer than the UPS runs.

I've seen this on about 6 of the 10 units I have.  Sometimes they do detect a bad battery and once I've changed it its good again for a while, then it may or may not detect the battery failure.

Maybe if you turn them off everyday they power on check would catch the bad battery, but to me that defeats the whole purpose.

I've replaced three with Belkins, too early to tell if they suffer this problem or not.  These are mostly on windows boxes.

--wally.

---

### Post by Zill on 2006-09-21
I bought a APC Back-UPS CS 500 about 3 years ago.  It has been nothing but trouble ever since! The unit frequently trips from mains to battery, with a loud click each time the relay operates. This occurs even when mains power seems perfectly stable, and even when the unit is set to its least sensitive mode.  If it "thinks" that power is missing for too long then it also starts beeping loudly - again often for no apparent reason - possibly OK for an office but really irritating for a home PC.
Finally, it went to battery and stayed there and would not go back to mains operation at all.  I contacted APC and was astonished to be told that they do not repair these units and as it was outside the two-year warranty period they would only sell me another one!  Forget it - I will take my chances without a UPS in future - I have great hopes for the robustness of the reiserfs file system I have now installed for my Ubuntu :-)

---

### Post by tagra123 on 2006-09-21
I made the script to power down the quick halt. Which still seems to preserve everything.  I had a belkin and its battery lasted 4 years before going bad,

A note to the other post about the unit frequently click on battery. I believe these units have an undervolt and overvolt protection.  We live in a rural area and notice this a couple of times each day. I figure its normal for our area.

New APC's have a replacable battery. Any battery with the same amperage should work. As far as the ones without a "replaceable" battery; the batteries can be replaced just not as easy.

 I'd test each unit every three months to make sure it shuts down properly.

If the monitor is hooked to the UPS, unless its a high amp battery, don't expect the power to last too long on any backup power supply. Add up the amps on the items you want to be protected and get a ups rated with those amps. 120 watts at 120 volts = 1 amp

---

