---
title: "Windows 7, Ubuntu 12, Raid1 with Mobo RAID?"
date: 2012-06-21
forum: Installation &amp; Upgrades
---

### Post by The Midnighter on 2012-06-21
Hi all,

Using M5A88-M, I created 2 raid1 (2x 500gb each) - Setting the SATA drives to RAID in the BIOS works beautifully. 

Trying to install Windows, but everytime I do with RAID set in the BIOS as the SATA drivers, Windows 7 continues to ask me for a driver for my CD/DVD drive, but if I select ACTI(?) Driver for SATA, it doesn't ask for this driver. 

The DVD drive is internal and connecting via SATA, I presume this is the issue but I'm not sure. Help?

---

### Post by darkod on 2012-06-22
Don't you think a windows forum is more appropriate for this question?

Check your mobo manual, often only some ports are part of the RAID, while others remain to be AHCI. If you have sata ports not part of the RAID function, try to connect the dvd drive there.

If that doesn't work, or you don't have non-RAID ports, try your luck on the windows forums.

---

