---
title: "Fresh install with 3ware 9650 controller fails to find disks"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by CraigUTS on 2007-05-22
Hi,

I have a new system with several disks in one raid array on a 3ware 9650 controller. 
I would like to use it with Ubuntu 7.04 but have read several posts discussing poor performance with VMware server. The all say that the 6.10 version is the latest stable release.

This is fine except that 6.10 doesn't have native support for the 9650 while the 7.04 release does.
I've been able to boot the system and format the disks using 7.04 so I know they work.

When I do the install of Server 6.10 it fails to find the disks.
I then followed the instructions on the 3ware page ([http://www.3ware.com/KB/article.aspx?id=15054](http://www.3ware.com/KB/article.aspx?id=15054)) to copy the 3w-9xxx.ko file to the disk (using PXE boot as I don't have a floopy drive).
However when i select the 3w-9xxx driver it still fails to find the disks.

Does anyone know if there is a log file I can check to find out why it is still failing despite the correct driver being available?

Many thanks,

Craig.

---

