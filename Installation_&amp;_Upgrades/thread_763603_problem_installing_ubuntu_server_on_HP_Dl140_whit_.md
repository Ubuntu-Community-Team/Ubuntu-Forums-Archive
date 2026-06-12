---
title: "problem installing ubuntu server on HP Dl140 whit raid controller"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by giliredbaron on 2008-04-23
Hi all,

I have a new HP proliant Dl140 g3 whit build-in raid controller.I configured a "RAID 1" disk.
But the installer can't "see" the raid disk, All I can see are two disks whit No raid... In older HP server I didn't had this problems.

Is there any way to make the ubuntu recognize the raid controller and "see" the disk as it supposed to be? 

Thanks,
gili

---

### Post by dstew on 2008-04-23
If it is a hardware-assisted software RAID, it is possible to install on it as a RAID. See the [_FakeRaidHowTo_]("https://help.ubuntu.com/community/FakeRaidHowto"). You install the dmraid program onto your Live CD boot, and it detects the RAID. Installing on the RAID is a bit of a chore. You have to hand-assemble the Ubuntu system, instead of letting the installer do it for you.

---

