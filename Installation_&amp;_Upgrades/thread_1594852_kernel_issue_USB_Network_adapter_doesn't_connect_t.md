---
title: "kernel issue: USB Network adapter doesn't connect to network after upgrade to 10.10"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by Magic_Spehar on 2010-10-12
Yesterday I upgraded my Ubuntu 10.04 (64bit) to 10.10 (64bit). Everything went fine except for the fact that my USB Network adapter (D-Link DWL G122) didn't connect to the network anymore.

I used the trial-and-error method and found out that the default kernel (2.6.35) in Ubuntu 10.10 causes the problem.  The USB network adapter is found when you do the command "lsusb":   Bus 001 Device 004: ID 07d1:3c0f D-Link System AirPlus G DWL-G122 Wireless Adapter(rev.E) [Ralink RT2870].  Unfortunately no connection is possible. 

I changed my GRUB menu and now the former kernel 2.6.32 is loaded and now everything works fine.

What could cause this issue with the new kernel 2.6.35 and what can I do about it? Any help much appreciated...

---

### Post by mörgæs on 2010-10-12
There are many reports in the fora that older kernels are working better than 2.6.35. If this solves your problem, just stick to the old one.

---

