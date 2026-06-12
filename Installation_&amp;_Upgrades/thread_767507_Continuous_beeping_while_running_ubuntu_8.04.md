---
title: "Continuous beeping while running ubuntu 8.04"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Klement on 2008-04-25
Hi,
I installed ubuntu and immeadiately notices continuous, high-pitched beeping, it repeats about once a second. I googled and found some references to the same problem. It is NOT coming from the pc speaker (pulled its plug to be sure). Also, strangely, it is cpu dependant. Run top -d 0 and its gone. Stop the top and its back. It's driving me nuts ... any ideas what could be causing this?

---

### Post by Klement on 2008-04-25
OK, I managed to get rid of the beeps by resetting my CPU frequency to default value. Somehow, the old ubuntu 7.10 could handle this but 8.04 can't. I found that powernowd-k8 complained about wrong BIOS data and googled for the info - and found out that overclocking the CPU causes some BIOSes to disable AMD's Cool'n'Quiet and/or provide no or wrong info about the CPU (or something like that).
The question remains, why did this work earlier (and still works in XP?)

---

