---
title: "Upgrade 7.04 to 7.10 no login"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by hgu on 2008-05-03
Hi,

I'm trying to upgrade from 7.04 to 7.10 so that I later can upgrade to 8.04. This is my MythTV machine (but I'm not using mythbuntu), that is connected to my TV. The motherboard: ABIT IL-90MV 945GT Mobile S478 HDMI mATX is connected to a LCD tv using the HDMI connection. I have used 915resolution to fix so that it can display at 1360x768.

When it rebooted it got to the light-brown screen which usually have a ubuntu logo in the middle, but then it stops without showing the logo and only the pointer-arrow. It was configured to do a auto-login before.

It is possible to switch to another tty with alt-ctrl-f1 and login. Everything looks OK, even mythbackend records in the background. I have also changed xorg.conf so that it uses a regular resolution, but it does not help.

During the upgrade I noticed that it rebooted directly somewhere at or near the end of the upgrade is that OK. Is it not going to ask if it may reboot? Trying to figure out if it missed some things at the end of the upgrade. From the logs I can't see what made it reboot, it was not mythtv, since I had temporarly disabled it. 

Any ideas of how to fix this? 

I rather not do a clean install of 8.04 since I have no place to backup my 800 GB of recordings.

---

### Post by hgu on 2008-05-03
I installed ubuntu 8.04 on a different partion on the disc, then I discovered that in the new grub menu there was a ubuntu 7.10 2.6.22 kernel that was not present before. When trying to boot with that image it just paniced. So it might be that the upgrade was interupted.

/Harald

---

