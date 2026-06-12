---
title: "Partition/X Server Errors - Edgy LiveCD"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by the_joker on 2006-11-28
I've attempted to upgrade from Dapper -> Edgy approximately 6 times now, and each time I'm having the same issues.

The first time the CD booted, everything seems OK. The Live CD boots to the desktop normally, the installer starts, but when I attempt to partition my drives manually, GParted hangs.


The second and subsequent times I tried to upgrade, the X Server was not working correctly.

Screen resolution was 640x480, and this was the only resolution available. I managed to reconfigure the X server, but I have no idea why it worked for the first boot, but failed for subsequent boots. The video card is an ATI Radeon 9800 Pro, with a 19" CRT monitor capable of 1600x1200 resolution (Dapper runs at this quite happily).

Any advice is appreciated. I've searched the forums, and found instructions for reconfiguring the X server, but no details on why it happens, or how to fix the partitioning errors.

Thanks for your help!

---

### Post by the_joker on 2006-12-03
Problem solved. After reading some other threads on this topic, I found that the dosfsck process was locking up. Killing that process allowed me to manually partition the drive without any further problem.

I still didn't figure out why the x server was preventing me from selecting any other resolution than 640x480 though.

---

