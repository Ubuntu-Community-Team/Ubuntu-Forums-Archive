---
title: "Ubuntu 7.04 Installation Woes"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by prayingmantis on 2007-07-03
Hi everyone,

I was hoping someone out there might be able to help out on this one! I appreciate it.

1. I tried installing/running the 7.04 64bit cd on my Core2Duo Intel 965 (Asus p5b) with 4 gb of ram and 8800 gts. Each time, the monitor went into powersave or standby mode without any way to get it back without a reboot. Interestingly, the hard disk and DVD were being accessed after the screen went to standby.

2. I decided to go for it and installed it under text only mode. That worked great.

3. I rebooted and tried to run it normally; again, the standby mode returned. This time, nothing was working in the background. Reboot required. 

4. On the next boot, I decided to try recovery mode. It started just fine, then hung on the two following lines:

agpgart: Detected Intel 965G chipset (blah blah blah 'cuz I forget the rest, sorry!)
iTCO_vendor_support: vendor-support=0


Any ideas  to get this thing to boot, either the live CD or the installed version? (preferred). Thanks so much for any help! Really appreciate it... if you need any more info, I'll gladly provide it :)
-Chris

---

### Post by louieb on 2007-07-04
Boot to recover mode and try this.
```
dpkg-reconfigure xserver-xorg
```
It probably the video that giving you a problem. See if the vesa driver will work.

---

