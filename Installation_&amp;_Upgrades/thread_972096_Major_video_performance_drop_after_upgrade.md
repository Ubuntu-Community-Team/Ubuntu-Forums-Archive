---
title: "Major video performance drop after upgrade"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by jonpz on 2008-11-05
Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
This graphics controller was working sweet under 8.04, but after an upgrade to 8.10 is running like ... well, you know.  I found that my xorg.conf section for device was set up rather generic, so I tried specifying the Driver as "intel", but that didn't seem to make a difference.  I tried some other options that found peppered about on this or that forum as well, to no avail.  The relevant lines in my xorg.conf file look like this now:
Section "Device"
	Identifier	"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Driver		"intel"
	Option		"UseFBDev" "true"
EndSection
I can't give any quantitative value for the performance drop, but compiz used to run the effects that I had enabled very smoothly, and now is very choppy... Google Earth is unusable, just looks like its puking on my screen.  Very frustrating, but I'd like to attempt a fix before I do a fresh install of 8.04 to roll back.  Anybody got any ideas?

---

### Post by jonpz on 2008-11-07
After getting absolutely nowhere with this, I've decided to roll back to Heron.  Hopefully the next (stable?!?) release will be better.  With all the problems that I've seen reported with this release and especially the problems I was having (which wasn't limited to the video, that was just one of the most immediate needing fixing), I'm really disappointed.

---

