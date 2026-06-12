---
title: "low resolution after upgrading NVidia driver on Ubuntu 12.04"
date: 2013-01-14
forum: Installation &amp; Upgrades
---

### Post by ethanjyx on 2013-01-14
Hi all,

I'm trying to install CUDA on my Ubuntu and installed the NVidia driver downloaded from NVIDIA's official website.

After reboot, my resolution was stuck at 640x480.

Things I've tried are listed as follows:
1. cvt 1200 800 60 and add Modeline to /etc/X11/xorg.conf
2. cvt 1366 768 60 and add Modeline to /etc/X11/xorg.conf
3. get other appropriate versions of drivers from NVIDIA website and install them
4. sudo apt-get install nvidia-current
5. sudo dpkg-reconfigure xserver-xorg

I tried them one by one but none of them worked...

Any advice? Thank you!

xorg.conf can be seen in the attachment.(this is the version after cvt 1200 800 60) 
System: Ubuntu 12.04

---

### Post by ethanjyx on 2013-01-14
Please help me!

---

### Post by efflandt on 2013-01-16
What video card do you have and what does **sudo lspci -v** show for your video, including modules?

It is usually easier to get things coordinated, working, and automatically updated with Ubuntu packages.  Since 12.04 seems to install nvidia-current during installation if it sees that you have nvidia, you could have gotten nvidia 304.64 drivers by just adding xswat to your repositories and checking for updates. [http://www.ubuntuupdates.org/ppa/ubuntu-x-swat](http://www.ubuntuupdates.org/ppa/ubuntu-x-swat)

But since you have been tampering with other install scripts and haven't said what you removed, if anything, before trying that, I am not sure how you can clean that up.  I ended up with bits and pieces of 2 nvidia versions once and ended up having to reinstall Ubuntu to fix it.  I imagine that /var/log/Xorg.0.log would show nvidia drivers not actually being used. Does **NVIDIA X Server Settings** show other available resolutions or that nvidia driver is not loaded?

**cvt** or **gft** do not return a modeline exactly 1366, but if drivers were working properly, a 1360x768 mode would work for a 1366x768 display.  And where did 1200x800 come from which seems like an odd comparison?  Some laptops are 12_8_0x800, but a mode proportional to 1366x768 would be 1280x720 (720p).

---

