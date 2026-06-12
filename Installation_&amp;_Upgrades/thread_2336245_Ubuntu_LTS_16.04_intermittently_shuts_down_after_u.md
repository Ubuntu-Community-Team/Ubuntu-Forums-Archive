---
title: "Ubuntu LTS 16.04 intermittently shuts down after upgrade from LTS 14.04"
date: 2016-09-06
forum: Installation &amp; Upgrades
---

### Post by luh3417 on 2016-09-06
Memory 7.8 GiB
CPU Intel® Core™ i7-3770 CPU @ 3.40GHz × 8 
Video GeForce GTX 750 Ti/PCIe/SSE2
OS 64-bit

Hi,

The upgrade from 14.04 had errors and did not carry out the final system check and did report possible fatal errors but the system rebooted after the upgrade and still boots up OK and runs perfectly except that about every few hours it shuts down/crashes.

I am attaching kern.log at time of last crashes which was pretty much Sep 6 22:00

If you need more log files etc please advise

---

### Post by luh3417 on 2016-09-07
Fixed. Completely removed vdr and removed /etc/init.d/mythtv-status.
These were running for no reason and seemed to be causing the shutdown

---

