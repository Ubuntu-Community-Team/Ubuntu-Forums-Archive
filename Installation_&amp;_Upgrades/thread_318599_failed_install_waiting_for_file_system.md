---
title: "failed install waiting for file system"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by milton1 on 2006-12-14
I've been running a network install because my cdrom does not work. The install made it as far as "select and install packages" and then failed. Grub never loaded. Install didn't finish. Now, I can use a floppy based grub to boot the system using /boot/vmlinuz and /boot/initrd, but the boot fails after hanging at "waiting for file system" I get an error message that the file system does not exist, and am dropped into an ash shell. Is there any way I can recover this and continue the install process? I'm hoping there is a way I can get to a proper shell and run something like "dpkg --configure -a" to finish the system configuration. I know all the packages downloaded; I just need to get them set up. Any suggestions?

---

