---
title: "uninstall video drivers before upgrading?"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by daryl314 on 2005-10-13
I'm not sure if I'm posting in the correct forum.  If I'm not, let me know . . .

When I was using ubuntu 5.04, I tried to get firewire video capture working by following the instructions in [https://wiki.ubuntu.com//HowToCaptureDigitalVideo](https://wiki.ubuntu.com//HowToCaptureDigitalVideo) .  however, it didn't work, and i found out that my issue was likely due to patchy firewire support in the 2.6.10 kernel.  when i followed the instructions in the wiki, it had me manually compiling and installing packages (DV playback controllers, a driver, and audio codecs).  It wasn't through apt-get, and I have no idea of what installing these did to my system.

My question:  Do I have to uninstall these somehow to upgrade ubuntu to 5.10 cleanly, or can I just upgrade directly?  I'm wondering if it could cause problems with firewire support if installing them in 5.04 didn't work and I leave them in my system when I upgrade.

Thanks!

---

### Post by mlomker on 2005-10-14
> I'm wondering if it could cause problems with firewire support if installing them in 5.04 didn't work and I leave them in my system when I upgrade.


I doubt that anyone can answer your question for sure.  Clean upgrades are always a safer bet...I had my share of issues and my setup was fairly plain.

That being said, installing kernel modules shouldn't hurt anything because the kernel will be replaced with a 2.6.12 version.

---

