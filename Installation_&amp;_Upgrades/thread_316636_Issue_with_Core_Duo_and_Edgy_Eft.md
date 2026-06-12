---
title: "Issue with Core Duo and Edgy Eft"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by gbraad on 2006-12-11
Sometime ago I upgraded from Dapper Drake to Edgy Eft. Almost everything seems ok, except for Avahi crashing on startup... but I accepted it. I had been running the 386 kernel without really knowing it... Due to this it doesn't run SMP like it did before. I changed to the generic kernel; At first I got the getting cpuindex for acpiid 0x1, can't access jobcontrol... but these were easily fixed. Now I run generic, with the linux-686-smp packages but still i only get results of running a single core machine. My laptop is a SZ2VP-X; the bios shows single processor, 2 cores. There is no option to disable the duo core functionality... CPU is a T2600. Sorry for not including the cpuinfo and uname (these got lost after trashing tmp).

---

