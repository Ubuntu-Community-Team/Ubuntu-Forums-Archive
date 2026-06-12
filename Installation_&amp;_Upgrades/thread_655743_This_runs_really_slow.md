---
title: "This runs really slow"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by Mindflux0 on 2008-01-01
I bought this laptop with vista on it (hp 6000, 1.7ghz turion, 2gigs ram) and, as expected, it runs like crap. hurray for vista.  So I figured I'd install linux on it to improve performance and somehow it did the exact opposite.  Ubuntu runs *slower* than vista.  Why????  In vista there's like a 2 second delay to open up firefox, in ubuntu it takes like twice as long and even hangs for a second or two when minimizing or switching windows.  It boots up 5 times faster, which is nice but why in the world does it run worse than vista?

---

### Post by ekh on 2008-01-10
Start System Monitor:

System->Administration->System Monitor

Select the tab: Processes

If "trackerd" eats excessive CPU time, you can remove "tracker" with Synaptic.

I removed tracker on both my portables, as the disk was very busy and the CPU consumption was 90%.

See:
[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/130817](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/130817)

The system monitor is yor friend helping to identify the proces slowing down your PC.

I saw a link sometime ago about optimization of Firefox, maybe you can find it to make your Firefox faster.

---

