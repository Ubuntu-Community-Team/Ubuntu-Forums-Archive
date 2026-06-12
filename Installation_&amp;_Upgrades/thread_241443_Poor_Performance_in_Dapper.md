---
title: "Poor Performance in Dapper"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by bmagill on 2006-08-22
My system is running too slow for the hardware that I have.  I hope for some suggestions as to where I might look.  For about 6 months, I was a happy breezy user.  Then, just before Dapper was released, there was a kernel update, don't recall any specifics, and the system bogged down.  I decided to wait it out and eventually upgraded to Dapper, hoping things would be better, but they were not.  It was bad enough that I went to Gentoo for a while and was really impressed with its performance, but not with the difficulty and time required to maintain it.  So, I am giving Ubuntu another run.  But, if I don't get this worked out, it will not be for long.

Firefox loads in about 15 seconds.
Openoffice will take about a minute to open.
General sluggishness.

This is a stock installation.  The only change I have made is adding the Nvidia drivers.

SOYO KT400 Dragon MoBo, using on-board sound, usb
AMD XP 1800+
756 RAM
Maxtor Hard Drive 60GB, relatively recent
Nvidia GeForce MX 440 (Using Nvidia Drivers)

I suspect DMA problems, but I cannot track it down.  hdparm -Tt was something like 60/30.  Hdparm tells me DMA mode is on.  I have played with hdparm settings, to no avail.

In the interim, I tried slackware and Gentoo, both blazing fast, both giving read/writes several orders of magnitude better than on Ubuntu.  I would have stayed had they not been so darned hard to maintain.  Free BSD also runs very fast on this machine.  Hope to find some solutions.  If nothing else, I might go bak to a basic Breezy installation and never update it, I still have the old disk!

---

### Post by ajgreeny on 2006-08-22
Did the sluggishness coincide with the Nvidia driver installation as it is the only thing you have added if I read you correctly?

Rather than going back to a breezy install, if you are going to do a clean install this time instead of an upgrade, I suggest a clean install of dapper will be better.  I have certainly found it to be much quicker than breezy, and overall a much smoother ride.

---

### Post by bmagill on 2006-08-22
> **ajgreeny said:**
> Did the sluggishness coincide with the Nvidia driver installation as it is the only thing you have added if I read you correctly?

Rather than going back to a breezy install, if you are going to do a clean install this time instead of an upgrade, I suggest a clean install of dapper will be better.  I have certainly found it to be much quicker than breezy, and overall a much smoother ride.

There was no difference in the system before and after Nvidia installation.  I was hoping it would help.  It did not.

Unfortunately, as I said, after initial problems with the Dapper upgrade, I left for a couple of months in favor of Gentoo, completely overwriting my Dapper installation (upgrade). Yesterday, after breaking my Gentoo and not wanting to go through days of compilation, I reinstalled Dapper from the iso thinking, too, that the fresh installation might make the difference.

Now, I sit with a shiny new dapper installation, pristine save the Nvidia addition (not to mention a little xorg problem that left me downgrading Xorg core, but that is another matter, referenced these forums).  It is still slow.  Again, my favorite suspect is DMA.  Drive performance in Dapper is definitely dismal.  Timed reads and writes are very poor, but DMA is on, according to hparm.  It might be a kernel setting.  Can I downgrade to the 2.6.12 kernel that the initial Breezy used?

---

