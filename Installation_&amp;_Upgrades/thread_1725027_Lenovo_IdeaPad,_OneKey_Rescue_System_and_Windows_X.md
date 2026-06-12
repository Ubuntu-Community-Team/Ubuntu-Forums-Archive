---
title: "Lenovo IdeaPad, OneKey Rescue System and Windows XP factory default..."
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by Z80A on 2011-04-09
Got my hands on this Lenovo IdeaPad S10-2 netbook on which I would like to make a full installation of Ubuntu (_not_ WUBI). Windows XP SP3 is preinstalled along with Lenovos OneKey Rescue System, which makes it possible to restore drive C: including restoring it to a a factory default state (*out of the box state*, no Windows user configured yet). The 160 Gbytes harddisk is split into 3 partions - I assume the last one (sdb3) is the one holding the OneKey functionality:
[INDENT]sdb1 NTFS (*drive C:*) 105 Gbytes boot
sdb2 Extended 29 Gbytes lba
sdb5 NTFS (*drive D:*) 29 Gbytes
sdb3 (*hidden drive*) - sdb315 Gbytes
[/INDENT]The way I read the documentation, using OneKey to make a backup on external optical media, restoring a Windows XP backup can be done (e.g. when replacing the harddisk, but I am not sure the factory default options is included. Can not figure out if merging sdb1 and sdb2 for an Ubuntu installation would destroy OneKey and the factory restore option.
 
The essence of my question; how do I make a full Ubuntu installation with as much possible disk space while preserving the OneKey functionality and the ability to make a factory restore of the Windows XP installation (in case I some day hand the machine over to someone not sharing my joy of working with Ubuntu).
 
By the way; is it correct that a wired Ethernet connection is needed initially, in order to get the right 3rd party WLAN drivers on the Lenovo IdeaPad S10-2?
 
Z80A

---

### Post by mikewhatever on 2011-04-09
You should probably by another hard drive and replace the original one.
As for the wireless, some cards (Broadcom ...) require downloading and installing proprietary drivers. There is a graphical tool for that in Ubuntu, but downloading won't work without internet connection. If your computer has an Intel wireless card (Intel 3945/4965), it should work out of the box.

---

