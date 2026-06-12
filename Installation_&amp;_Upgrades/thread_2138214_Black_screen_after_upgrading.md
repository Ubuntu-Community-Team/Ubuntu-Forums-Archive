---
title: "Black screen after upgrading"
date: 2013-04-23
forum: Installation &amp; Upgrades
---

### Post by Abbobo on 2013-04-23
Hi,

I just upgraded from 12.04 x64 to 12.10. After reboot I got GRUB > splash screen > Nothing. I can log in by editing the grub command to add "text" then use command line to access the system, but I don't seem to be able to get the display running. I've googled countless messages and most responses centre around reinstalling nvidia-current however this isn't working for me. (also worth mentioning I dont have an nvidia card, its Intel HD 4000 graphics)

I don't really know where to start on this - could someone help me try to find out what is wrong and how to fix it?

Thank you
Abby

---

### Post by dino99 on 2013-04-23
your issue seems related to the greeter; are you using gdm or lightdm ?

sudo dpkg-reconfigure -phigh -a
( be patient, can take a while)

---

### Post by Abbobo on 2013-04-24
lightdm but I also tried changing to gdm. My xorg log said no drivers and no displays were found. I ended up just doing a reinstall of 12.04. I found a few pages saying that there is poor support for the intel 4000 drivers still so I'm just going to stick on 12.04 and try live disks when new releases come out.

---

### Post by MAFoElffen on 2013-04-24
At the Grub Menu... Boot from a previous Kernel version. Then join one of the bugs for it in Launchpad. Intel GPU drivers are boinked at the moment.

It's the xserver-xorg-video-intel driver. Follow this thread:
[http://ubuntuforums.org/showthread.php?t=2128691&page=5&highlight=xorg+intel+bug](http://ubuntuforums.org/showthread.php?t=2128691&page=5&highlight=xorg+intel+bug)

3 work-arounds (not fixes yet)- Boot from earlier kernel, remove the xorg driver and install an earlier version (pinning it to not upgrade), or go edgers ppa (whic is still not stable for some)...

---

