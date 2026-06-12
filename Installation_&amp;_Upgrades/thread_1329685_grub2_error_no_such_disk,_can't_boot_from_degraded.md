---
title: "grub2 error: no such disk, can't boot from degraded raid array"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by jaygo on 2009-11-17
Problem:
after losing a drive from my raid array, grub2 won't boot and drops me to its rescue prompt.

Description:
I installed karmic into two raid10 arrays (softraid / mdadm), md0 (/boot) and md1 (/root, swap, /home). The array currently has members 0 & 2 up, which means it's running raid10 with only two drives -- essentially in raid0. Just to reiterate, I have a complete array and am able to assemble it in a liveCD session and see the data in boot, root, and home.

I'm not sure what's the best route. I have my data backed up but repairing grub2 rather than reinstalling would save me a few days of hassle. Should I just reinstall grub2 from a liveCD?

---

