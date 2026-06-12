---
title: "Upgraded to saucy 13.10. Now freezes on boot when using kernel newer than 3.8"
date: 2013-12-11
forum: Installation &amp; Upgrades
---

### Post by stbvision on 2013-12-11
Hello everyone!



I upgraded lub[SIZE=2]untu 12.10 -> 13.10. After this I'm unable to boot with current kernel version. Computer freezes on "lubuntu"-screen with white/blue dots and I cannot switch TTYs using key-combinations (Ctrl-Alt-F1 - F6[/SIZE]).

When I investigate freezing-point using grub2's recovery mode -option I found out that computer freezes at line "starting cups-browsed - Bonjour remote printer browsing daemon [OK]".


Machine boots fine to 13.10 with older kernel (3.8.0-31-generic) but not with kernel versions newer than this.


Specs:

-AMD Sempron Processor 3300+
-766MB memory
-ATI Radeon 9600 


I can use computer with this workaround, but I like to figure out more stabile solution. Is there any changes to get newer kernel to boot with my hardware?

---

### Post by mörgæs on 2013-12-11
This happens from time to time.
A fix might be in progress. You could just wait and see what the next kernel update brings.

---

### Post by stbvision on 2013-12-12
This happens every time to me with this computer.

I have tried to investigate is this a known bug, but I haven't found out for sure.

I'm glad to hear that this is a common problem, so this could be fixed in future kernel versions.

---

### Post by mörgæs on 2013-12-12
I can't tell if this particular problem is common, but the general class of problems (a new kernel introducing a bug) is. The developers can't test a kernel on any given combination of hardware.

I wouldn't report it for now, but if it persists through a couple of new kernels please do.

---

