---
title: "Ubuntu 8.04 Nvidia driver problem"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by Gunther82 on 2008-05-01
Hey

I'm having a problem enabling compiz. When I go to Appearance Preferences - Visual Effects and enable Extra, a pop-up asks wether I would like to enable NVIDIA accelerated graphics driver (latests cards). I press enable, and it downloads a driver, then the following error accours: 

**E: nvidia-glx: underprosessen post-removal script returned error status 2.**

Then, whenever i go to the package manager to install/uninstall something, it lists nvidia-glx for removal, but displays same error when it is trying to remove it. Hence I can't install anything else.

My graphic card is a GeForce 7600GT.

By the way, I'm a complete noob to Linux and Ubuntu, i have some experience with windows but that's no good now.

I've searched the forums, but have not been able to find a solution for my problem. I anyone can tell me which log files to post to better describe the problem that would have been nice. Or even better, tell me solution for the problem :)

Any help would be greatly appreciated.

---

### Post by Gunther82 on 2008-05-01
There seems to be a solution for the problem, however, I tried these commands; they did not work for me.

sudo dpkg-divert --remove /usr/X11R6/lib/libGL.so.1
sudo dpkg-divert --remove /usr/X11R6/lib/libGL.so.1.2
sudo dpkg-divert --remove /usr/lib/xorg/modules/libGLcore.so
sudo apt-get install nvidia-glx-new

Hopefully some of you knows what to when you reads this, if you do, please post directions for med.

Link to forum with solution:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/130208](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/130208)

---

