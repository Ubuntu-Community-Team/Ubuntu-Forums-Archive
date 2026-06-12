---
title: "Partitioner doesn't detect disk drive"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by Pragmatictwitch on 2006-08-12
I am attempting to install Ubuntu on my computer for my first time.  My roommate has installed Ubuntu on his desktop and laptop, hasn't had any problems in installing his, but is as equally stumped.  This is my system:
Dell E510
1.0gig DDR2 SDRAM
160gig SATA IDE HD (not RAID)
(40gig free space (not NTFS) partition for Linux install)
The following has been done:
*Install Dapper Drake from Live CD
(Also attempted ACPI off) 
*Install Dapper Drake from Alternate CD
*Install from Edgy Eft
*Verified CD content to rule out CD error
In every instance it cannot find the hard drive in the partitioner. But the harddrive and its partitions show up on the device manager.
Also; I've mounted the NTFS partition via FSTab and I can read files fine. However the "disks" utility and partitioner doesn't freeze or lock up, but simply doesn't read anything. As a result, I cannot install to the harddrive.
There are no warnings or error messages.
I hope this isn't a bug, and hope it is a simple fix.
Is there anything else I should be trying?

---

### Post by taipoh on 2006-08-12
Likely your SATA controller is to blame.  Here's a thread fixing Promise ones;

[http://www.ubuntuforums.org/showthread.php?t=126199](http://www.ubuntuforums.org/showthread.php?t=126199)

---

### Post by Pragmatictwitch on 2006-08-12
Thanks, but I'm not sure that I'm running a Promise SATA Controller.  This is what my hardware manager says I have: 
Intel 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller - 27CO

Is there any known specific information on this type?

---

### Post by Pragmatictwitch on 2006-08-12
An update:
the disk controller is the aic7xxx, and we attempted the noprobe command in the controller with no luck.

---

