---
title: "Install Graphic Mode - Safe Graphics not safe?"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by waynep on 2006-10-27
I had to install 6.06 using safe graphics mode becuase I installed it into a virtual machine. It worked great. 

Along some 6.10 and safe graphic mode is not safe anymore. It seems that it's defaulting to 32 bit depth. I need it be 16 bit due to the Virtual PC limitations. I have tried Safe graphic mode and it does the same thing as normal mode. 

I had the same issue with Fedora Core 6. For that I installed it using text mode install. I then changed the xorg.conf file before altering inittab to start in X mode. 

How can I install 6.10 in a lower bit depth graphic mode, or a simple text mode?

-wayne

---

