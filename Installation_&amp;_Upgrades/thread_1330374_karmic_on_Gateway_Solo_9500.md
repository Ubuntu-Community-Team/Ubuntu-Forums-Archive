---
title: "karmic on Gateway Solo 9500"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by fredfox on 2009-11-18
This is kind of a continuation of the thread:

Gutsy on Gateway Solo 9500 (which was never solved)
[http://ubuntuforums.org/showthread.php?t=605091](http://ubuntuforums.org/showthread.php?t=605091)

I actually installed jaunty on said machine then installed karmic.

The machine Gateway Solo 9500 with 512MB ram and 20gig HD, good battery.

1. The live CD, full graphic install worked fine. The install was normal.

2. On reboot, fschk would complete and then the the machine would power off. By adding acpi=off, to the kernel line in grub, the machine would successfully boot about 50% of the time with jaunty. With karmic, it would successfully boot about 10% of the time.

3. I tried the gentoo base install CD for comparison. It has the same problem, booting about 10% of the time even with acpi=off noapic, nolapic, nodetect kernel options.

4. I use PING ([www.windowsdream.com](www.windowsdream.com)) for drive imaging, so I tried that on the machine. Boots just fine, probes the hardware, fully functional.

Question: what is different between the install CD kernel configuration or initialization and the kernel configuration and initialization that is installed in UBUNTU that could cause this power off during boot?

I am having trouble identifying the step during boot that triggers the power off.

---

