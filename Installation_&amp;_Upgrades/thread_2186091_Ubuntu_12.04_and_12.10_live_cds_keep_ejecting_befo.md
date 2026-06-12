---
title: "Ubuntu 12.04 and 12.10 live cds keep ejecting before installing."
date: 2013-11-05
forum: Installation &amp; Upgrades
---

### Post by silverhaze06 on 2013-11-05
I have an hp pavillion g6 with amd-3400m apu. I recently had to do another recovery of my windows side and reinstall everything. this has happened once before. But this time when i try to reinstall ubuntu 12.04 or 12.10 as a program within windows, it will eject the cd and tell me to remove media and reboot after clicking install inside windows. when it reboots windows just starts up normally.

I installed both cds before with no problems, (and they were both the 64bit amd versions), the md5 checksums are also fine like they were before.

I would try a later version on cd but i have no more left to burn and i can never seem to get a usb installation to work at all either.

---

### Post by fantab on 2013-11-05
Is this a new laptop? What version of Windows did you install? Did it come pre-installed with Win8?
Check in your BIOS/UEFI to see if CD/DVD is bootable and set to boot first?

Wubi is not a recommended way to install Ubuntu. In fact, its not working with since ubuntu 13.04, and it won't work with Windows8. 
Instead of Wubi, allow me to recommend full Ubuntu install, a true dual-boot, on its own partition.

---

