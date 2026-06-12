---
title: "Natty Firefox Performance Improvement via Oracle (Sun) JRE"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by TechnoChick on 2011-05-25
I recently upgraded my Dell Vostro 1700 laptop from a much older version of Ubuntu to Natty 11.04. I think I'm going to like the new Unity desktop, especially now that the toolbar on the left-hand side auto-hides.

I had to use "Additional Drivers" to reinstall the proprietary NVIDIA graphics driver (version 173). Additional Drivers reports "No proprietary drivers are in use on this system." and "This driver is activated but not currently in use." But I've seen in other posts that this is a jockey messaging problem and the driver is actually being used. I tried to install and run the "(version current)[Recommended]" NVIDIA driver but it didn't work for me.

I noticed that the Natty Unity desktop seems to be slower or less responsive than the previous Gnome based releases. I especially noticed this when viewing complex webpages with Firefox (Version 4.0.1 / Canonical 1.0). I experienced "lags" lasting as long as 30 seconds during which I could not scroll the page or enter text.

I found the following link in an article in this forum that suggested replacing OpenJDK and the IcedTea plugin with the Oracle (Sun) JRE:

[Easy Linux tips project - Oracle (Sun) Java JRE]("http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU")

I have not experienced any Firefox "lags" since making this configuration change. YMMV. I didn't save a link to that forum thread, but I am indebted to that member for sharing a link to this useful information. Thanks!

---

