---
title: "Partitioner does not recognise my raid"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by Highlordbob on 2010-01-06
I am completely new to anything besides Windows and would like to give Ubuntu a try but I cannot get the installer to recognise my raid 0. I am not sure what the raid driver is but its the Intel controller on a evga x58 classified mobo.

---

### Post by darkod on 2010-01-06
For raid you need what is called Alternate Install CD, not the standard desktop cd.
Get it here:
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

**Alternate install CD**

  The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:
  
[LIST]
[*]setting up automated deployments;
[*]upgrading from older installations without network access;
[*][COLOR=Red]LVM and/or RAID partitioning;[/COLOR]
[*]installs on systems with less than about 256MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably).
[/LIST]
Note that the alternate installer is text based. During the install process you will not have a GUI, just text based screens. The system that will be installed will have the standard desktop GUI.

For fakeraid (motherboard bios raid), also read this:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Highlordbob on 2010-01-06
Should i create a partition in windows first so that i cant accidentally mess up windows or should i just let the partitioner do this for me, because i still want to keep my windows running duel boot.

---

### Post by Highlordbob on 2010-01-06
Ok i decided just to go ahead and try to install it but when i get to the partitioner it does not show me any partitions and skips all the menus. It goes strait to asking me if i want to finalize and shows nothing where the list of partitions should be.

---

