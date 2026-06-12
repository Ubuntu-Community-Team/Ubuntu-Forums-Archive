---
title: "Two screens not working on first boot"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by Epimetheus on 2007-09-19
Im having a bit of a problem, whenever i start ubuntu from livecd or first time after installation, well basically anytime when I have done nothing to configure xorg, I get two screens similar to 70s LSD-trip, which might be cool to some, but definitely not useful. Luckily Ive learned enough linux that i can fix it by going into tty1, install nvidia drivers, run nvidia-settings and restart X but since Ubuntu is supposed to be easy to use this might be of some concern.

System:
First noticed on Ubuntu 7.04 (same problem om 7.10 tribe 5 livecd)
Nvidia graphicscard
amd K9 processor
Dual-screen setup with TwinView (LG-screens)

---

### Post by aJayRoo on 2007-09-20
I don't really have anything to add except that I have the same experience whenever I try to install or run a live CD without first unplugging my second monitor. I usually install with one monitor then plug in the second after first boot and configure twinview using the nvidia-settings application. This happens when installing 7.04 and when running live CDs of 7.04 or 7.10 tribe 5. I didn't have a twin monitor setup when using 6.10 so I cannot confirm that this problem was introduced in 7.04.

---

### Post by Epimetheus on 2007-09-20
Thats exactly the same problem i have, I'm just too lazy to unplug the second monitor and just install the drivers instead :P

---

