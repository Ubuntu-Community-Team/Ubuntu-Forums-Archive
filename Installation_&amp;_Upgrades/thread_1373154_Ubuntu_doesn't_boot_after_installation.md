---
title: "Ubuntu doesn't boot after installation"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by kdardio2415 on 2010-01-05
I'm trying to dual boot 9.10 with Vista on an HP Pavilion Slimline (AMD64).  I've tried both booting from a disk and using Wubi, and neither has worked.  Booting from the disk takes me through the screen where I can choose to try Ubuntu without installing, but after selecting that, the desktop didn't load, the screen just went to black.

I decided to try Wubi, and it went well enough.  Everything in windows worked, and upon rebooting, it was able to finish checking the installation.  After one more reboot, I selected Ubuntu from the Windows boot manager, and then the grub command prompt appears.  I can't seem do anything after that except reboot.

I have no idea what's going on with this computer.

---

### Post by sanderj on 2010-01-05
Can you boot off the 9.10 CD with Safe Graphics after pressing F4 in the start screen. See [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) for instructions

If not, can you remove "quiet splash" from the boot options, to see what goes on during boot? See [https://help.ubuntu.com/community/BootOptions#Changing%20the%20Boot%20Option%20Configuration%20Line](https://help.ubuntu.com/community/BootOptions#Changing%20the%20Boot%20Option%20Configuration%20Line)

Finally, have you tried booting a 9.04 CD?

---

