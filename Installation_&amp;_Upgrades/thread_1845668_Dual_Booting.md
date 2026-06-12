---
title: "Dual Booting"
date: 2011-09-17
forum: Installation &amp; Upgrades
---

### Post by warich on 2011-09-17
Hello, I know that this is probably an obvious answer, but I have a tough problem, considering I'm fairly new to Ubuntu. I installed Ubuntu onto an external HD, Seemed simple to me, Since I'm on a laptop My HD space is limited highly, I wanted a large Partition so I figured to put it on my 320GB Seagate. It is attached to a 4Port Externally powered 2.0 Hub. Here's my problem, it will not boot Ubuntu Unless im plugged into the Hub and the Hub is working on external power. I get a "/host/ubuntu/disks/root.disk not exist. Dropping to shell" and then it just fails. I have searched Google for a long time and I try to avoid forums as much as I can. But at this point I'm just about to give up. Frustration is at the maximum, I want to use the Ubuntu on the HD without the powered hub, PLEASE help me.

---

### Post by oldfred on 2011-09-17
Welcome to the forums.

Many computers only have so much power for USB ports. That is why a hub has to have external power to fully power any device that needs more power or is not self powered.

If it is looking for root.disk, you have installed wubi which uses the Windows boot loader and runs inside a NTFS partition. That is fine for a longer test of Ubuntu than what you can do with a liveCD and makes it easy to delete, but it is not true dual boot.

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by warich on 2011-09-17
Thank you a lot, I didnt know that Wubi was mainly used for short term, I appreciate the guide as well. I just read through it. This IS a stupid question, but it seems to me like it wants me to totally reinstall the ubuntu, i want to have all my current settings/files/utilities w/o removing them. How can I keep them, I appologize if this is a bad question.

---

### Post by Mark Phelps on 2011-09-17
Just so you know ...

The requirements to have additional power supplied to the USB hub to run the drive is independent of the filesystem and/or OS on that drive.

Meaning, if you reformat it and install UBuntu to that drive, you will STILL require the hub to be powered to use the drive.

---

### Post by Blasphemist on 2011-09-17
See this thread for how to convert the wubi install to a full installation. [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

