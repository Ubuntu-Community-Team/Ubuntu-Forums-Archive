---
title: "After install system reboots"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by sundar80 on 2006-12-12
Hi

I had installed Ubuntu 6.06 successfully.After I start the system, it asks options to boot which OS like kernel, kernel (recovery mode) and windows XP. When i select kernel and recovery mode also, it says booting kernel and system reboots repeatedly. What is the solution.

---

### Post by az on 2006-12-12
> **sundar80 said:**
> Hi

I had installed Ubuntu 6.06 successfully.After I start the system, it asks options to boot which OS like kernel, kernel (recovery mode) and windows XP. When i select kernel and recovery mode also, it says booting kernel and system reboots repeatedly. What is the solution.

Are you trying to install Ubuntu using the server cd on an old computer?

If so, boot the live cd again, chroot into your install and run

sudo apt-get install linux-image-386

The server kernel does not run on anything less than a 686.  When you try to boot the server kernel on a pentium one, it can just freeze or constantly reboot as you describe.

Is this the case?

---

