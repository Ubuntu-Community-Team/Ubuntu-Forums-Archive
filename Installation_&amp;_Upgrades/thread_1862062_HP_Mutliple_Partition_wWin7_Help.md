---
title: "HP Mutliple Partition w/Win7 Help"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by RayJer on 2011-10-16
Hi. I'd ultimately like to switch from Windows to Ubuntu but first wish to dual boot.  I have an HP 8560w laptop (with AMD M5950 graphics card) that boots 11.10 from the USB perfectly. Upon installing to hard drive, the "Install along side windows" option does not appear.  This seems to be an issue with the additional paritions present with the standard HP/Win7 installation.  It's a brand new laptop with plenty of space available and I don't mind shrinking and/or creating new paritions but request assistance on the proper procedures and tools to accomplish this.

Any help/pointers is greatly appreciated. 

Currently, there are 4 partitions named C, System, HP_Tools and HP_Recovery.  In my old days of using SysV Unix, we typically created a /swap, /usr and / file system... Things are more advanced now and there are far more file system types to choose from.  BTW: I would like to have an encrypted /home directory.

Regards
Ray

PS:  Linux has come a long way over the years -what a great effort!

---

### Post by 2F4U on 2011-10-16
You cannot have more than 4 primary partitions on one hard drive. So, if your existing partitons are primary partitions, that is the reason why the installer doesn't offer you to install alongside Windows.

---

### Post by RayJer on 2011-10-16
> **2F4U said:**
> You cannot have more than 4 primary partitions on one hard drive. So, if your existing partitons are primary partitions, that is the reason why the installer doesn't offer you to install alongside Windows.

2F4U,

Yes... after a good bit more of reading, I discovered what you mentioned...  The recovery disks that came with the computer do not work and HP will send me new ones -and I won't be surprised if those don't work either.  Anyhow, the laptop itself is very nice and I wish to run Ubuntu and Linux so I'll be forced to purchase a retail copy of Win 7, wipe-out the drive and re-install the OSs.  -Just did this on my son's desktop and it works just fine.

Thanks...

---

