---
title: "Hardware Migration question"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by grossb1 on 2007-12-01
So I had Ubuntu (not sure what version, somewhere close to the latest, upgraded a couple of months ago) running on a tbird 1.2.  Unfortunately, that computer died.  

I tried hooking up the hard-drive to a new computer, but it failed booting the agp440 device.

What do I need to do to get my prior Ubuntu installation to run under a new hardware configuration, short of re-installing?

---

### Post by heatpumpcontrol on 2007-12-01
I don't really think you can bring your HD to a new pc and get it to run. If most of the same hardware is on the new one ie: Video Card, Motherboard, Memory and type, LAN cards and so on, then you might get it to work...partially. 

First try to make sure that the video cards are the same. I'm new to Linux and it seems that if your video cards are different then you'll have to start with those settings so that you can at least get your video up.

do a:
lspci (that's a lower case L) and see if the hardware listed matches what you had on the old pc.

Otherwise, you can reinstall the O/S and provided you partitioned your /home directory, you will keep your settings during the re-installation. Just make sure you don't format your /home directory during the install.

---

