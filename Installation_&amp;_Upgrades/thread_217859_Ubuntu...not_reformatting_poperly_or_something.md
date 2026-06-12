---
title: "Ubuntu...not reformatting poperly or something"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by stuh505 on 2006-07-17
Ubuntu was working for me ok, I had finally got wireless up, then everything crashed.  It had something to do with wireless.  I rebooted and when I did gnome was completely unresponsive.  I reinstalled, tried setting up the wireless again, and the same problem happened.  So I reinstalled again...but THIS time, gnome was frozen even before making any changes.  Keep in mind that I have been setting to "reformat" each time...I have installed 2 more times, both with the same results.  Ridiculous!

---

### Post by az on 2006-07-17
> **stuh505 said:**
> Ubuntu was working for me ok, I had finally got wireless up, then everything crashed.  It had something to do with wireless.  I rebooted and when I did gnome was completely unresponsive.  I reinstalled, tried setting up the wireless again, and the same problem happened.  So I reinstalled again...but THIS time, gnome was frozen even before making any changes.  Keep in mind that I have been setting to "reformat" each time...I have installed 2 more times, both with the same results.  Ridiculous!

This happened to me once.  I was using a realtek wireless card which only worked with ndiswrapper until they started to include the linux native driver.  The fact that two drivers were vying for the same hardware made the system crash.

You can either remove ndiswrapper or blacklist the linux native driver.

Exactly what wireless card?

---

### Post by stuh505 on 2006-07-18
It's a BCM4306 (rev3)  (broadcoam wireless) card.

That is a good avenue I will explore.  Can you explain what happened to you more precisely?

The 2nd and 3rd installs went properly.  I don't understand why the 4th, 5th,  and 6th installations gave me a corrupt version of gnome that could not load properly.

I think that it may not actually be reformatting properly.  When I try to reformat using GParted or QTParted on Knoppix they both tell me the drive is mounted or in use or something so I'm thinking that the installer's reformatter might not actually be working.

I just popped in an XP CD and I am doing a DEEP format to NTFS over the entire filesystem.  Then I will try repartitioning it and formatting to reiser in another ubuntu install.

---

