---
title: "Recovering from Crash while running Update Manager"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by jcobban on 2010-01-07
I was running the Update Manager when my system froze due to the failure of Karmic to support motherboards using the Intel 845 chipset.  Although the update did not complete when I rebooted and invoked Update Manager it reported that the system was up to date.

How do I reset the system so that I can install the updates?

---

### Post by jcobban on 2010-01-07
> **jcobban said:**
> I was running the Update Manager when my system froze due to the failure of Karmic to support motherboards using the Intel 845 chipset.  Although the update did not complete when I rebooted and invoked Update Manager it reported that the system was up to date.

How do I reset the system so that I can install the updates?

I may have just answered my own question.  I went into a terminal session to perform an unrelated install, and a message appeared that an update had been interrupted and instructing me to issue "sudo dpkg configure -a" to recover.  When I issued that command it appears to have completed installing at least a portion of the pending updates, including the -17 kernel.

---

