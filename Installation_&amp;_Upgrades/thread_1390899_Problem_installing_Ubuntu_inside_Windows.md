---
title: "Problem installing Ubuntu inside Windows"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by sc1 on 2010-01-26
Hi, 
 
I downloaded Ubuntu 9.10 x64 Desktop and burned the ISO to cd. 
 
My config is the primary hard-disk has basic layout and 2 primary partitions:
(a) c: drive containing Windows Vista Ult x64
(b) u: drive formatted to NTFS where Ubuntu is supposed to go into.
 
 
I tried 2 installation options:
1) Install inside Windows. 
Installation proceeded to copy files to u: drive. Then it prompts to reboot and when I did so, it continued to complete setup. It was able to synch time from the server etc. then suddenly an error "No root filesystem is defined, Please correct this in the partitioning menu". But the dialog box keeps reappearing immediately after I clicked OK and can't get to the partitioning menu. No other keys responded. There was nothing else I could do but to boot back into Windows and uninstall ubuntu.
 
2) Installing directly from booting into the CD.
It was able to boot into the Ubuntu cd. There was a wizard with about 6 steps in total.
The first few was setting locale, keyboard etc. On step 3(or 4) it detected only 1 of the 4 drives (SCSI mode0), as will persist in installing onto sdc1. I need it to go into sdb2 where the u: drive is. I went into the Demo mode, and ubuntu started up and I could use the file browser to see all 4 drives including sdb2. But when I clicked on the "Install Ubuntu" icon on the desktop, the same wizard appeared but on step 3(or 4) it still detected only sdc, not sdb nor even sda, sdd.
 
Please can someone help me get ubuntu installed in either way. 
Thanks.
 
Steven

---

