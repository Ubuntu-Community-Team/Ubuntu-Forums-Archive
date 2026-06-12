---
title: "Trying to install Ubuntu 22.04"
date: 2023-07-24
forum: Installation &amp; Upgrades
---

### Post by swtom on 2023-07-24
During installation of Ubuntu 22.04 I get this message. "Block probing did not discover any disks.  Unfortnately this means that installation will no be possible." I am trying to install it on the the ASUS vivoPC VM40B desktop computer.  I did install Ubuntu Desktop before with no problems.  Any ideas.
Thanks
SOLVED the problem. Hard drive wasn't seated properly.

---

### Post by Rubi1200 on 2023-07-24
Hi and welcome to the forums :-)

Are you trying to install the server version?

If yes, take a look at this bug report and possible workaround:
[https://bugs.launchpad.net/subiquity/+bug/1910531](https://bugs.launchpad.net/subiquity/+bug/1910531)

---

### Post by MAFoElffen on 2023-07-25
Interrupt your boot process to get install your BIOS setup and go to the SATA mode setting. See if it is set to "RAID" or "AHCI". It should be set to "AHCI" for the Installer to see your storage disks...

*** Importat: If you have Windows installed on this machine, post back before changing that setting, and I will give you further instructions on what to do before changing that setting.

---

