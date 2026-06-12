---
title: "Failed upgrade after internet drop: 12.04 to 12.10"
date: 2013-02-26
forum: Installation &amp; Upgrades
---

### Post by jbuczek on 2013-02-26
I started the upgrade from 12.04 (AMD64) to 12.10.  Part way through my internet connection went down (wifi). The software update noticed and shut down gracefully saying it would save all downloaded files.

When the ISP restored service I started the update which immediately reported a new update (something about java plugin handler, I think).  Since the upgrade recommendations had said to install all current updates first and I assumed the updater knew what it was doing, I allowed it to proceed.  During the final phase (notifying) it hung.  After an hour I force quit and rebooted.

Now the updater reports "not all updates can be installed. Run a partial upgrade to install.... etc." and comments that this can be caused by a "previous upgrade which didn't complete". When I authorize a "partial Upgrade" it reports "unable to get exclusive lock" and aborts.

Any suggestions?

---

