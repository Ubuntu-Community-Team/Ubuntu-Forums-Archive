---
title: "CPU usage down but battery usage WAY UP after upgrade?!"
date: 2013-10-08
forum: Installation &amp; Upgrades
---

### Post by shiraz dindar on 2013-10-08
Has anyone ever seen this?

My Compiz has chewed up a lot of CPU since I started with 11.04 on my laptop. It was still happening with 13.04, along with more frequent system hangups which I believe were due to Compiz.

Seeing as to how there are significant Compiz changes in 13.10 and I read that even without Mir/Xmir enabled, there are Compiz improvements, I decided to do an upgrade to the beta 13.10.

Sure enough, my screen issues are gone, and my CPU usage is lower due to the lower Compiz (everything else seems about the same, running htop as root to monitor). Load is really low, cpu temperature is low (less fan than ever).

YET my battery life has dropped from about 3.5 hours to less than an hour (the estimates are off, I believe because it's using battery stats which include pre-upgrade, but ultimately I'm looking at about 25% of the battery life that I had before)

This seems totally counter intuitive. I've ran powertop to see if it would show me anything that htop doesn't, but it doesn't. 

Even with screen brightness all the way down and my 2nd HD spun down, this update has caused that.

I realize 13.10 is still in beta but this is a bit surreal. Has anyone ever experienced anything like this?

Thanks,
Shiraz

---

### Post by shiraz dindar on 2013-10-08
UPDATE: for some reason, I missed noticing this in Powertop -- Display Backlight uses a whole 10W at full brightness, and 8W at minimum brightness. This is on a mere 14" screen. When I plug into my external monitor via HDMI, Display Backlight usage goes UP to 12W. Do these sound normal? The display brightness is more than 5 times the power consumer than my next biggest consumer (the wlan). I understand this order to be normal, but not the size of the gap.

Perspectives appreciated!

---

