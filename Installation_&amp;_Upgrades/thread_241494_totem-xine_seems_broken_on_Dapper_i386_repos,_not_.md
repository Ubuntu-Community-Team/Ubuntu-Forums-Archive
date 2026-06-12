---
title: "totem-xine seems broken on Dapper i386 repos, not tried other archs"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by abc1987 on 2006-08-22
Hi there,

I've reinstalled Dapper i386 on my laptop and uncommented all the relevant lines in sources.list.

One of the first things I do in a new installation of Dapper is change the multimedia backend from gstreamer to xine, including installing the totem-xine package, so that I can play DVDs in totem and also cos I find it easier to configure with various non-free codecs.

Unfortunately, having had no problems getting totem-xine in the past, I now find that I cannot have it and the totem package installed at the same time, and with just the totem-xine package installed Totem closes immediately after being run. This did not happen before when the packages would install alongside one another happily.

I also noticed that where the totem-xine package is listed in Synaptic there is now no Ubuntu icon or other info displayed for the package unlike in the past. Everything does come up correctly for totem and totem-gstreamer, and most other packages.

Could somebody please tell me why this might be and what can be done to fix it or where else I could obtain a working version of totem-xine for i386? I also plan to install Ubuntu AMD64 on my Athlon 64 desktop.

Thanks for your help,

Alastair

---

### Post by abc1987 on 2006-08-22
Update:

I looked into the issue further and found that the version of totem-xine on the repos is older than that required by the totem dummy package (1.4.1 whilst totem needs >=1.4.3). So someone needs to modify one or other of those packages to fix the problem. I'm guessing totem-xine since now I realise totem is a dummy package, this must mean there's some kind of bug in totem-xine causing it to close - but if totem is a dummy package totem-xine should work regardless and doesn't - so totem-xine needs updating.

---

