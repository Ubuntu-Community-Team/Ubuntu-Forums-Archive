---
title: "Dual booting with Windows Vista"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by hypersoar on 2006-06-13
I recently installed Windows Vista Beta 2 on a machine with Ubuntu installed. I gave it its own NTFS partition and reinstalled Ubuntu (after installing Vista). After the reinstall, GRUB shows up with only Ubuntu options. No Windows. 

Anyone know how to fix this?

---

### Post by EndGame on 2006-06-13
[QUOTE=hypersoar]I recently installed Windows Vista Beta 2 on a machine with Ubuntu installed. I gave it its own NTFS partition and reinstalled Ubuntu (after installing Vista). After the reinstall, GRUB shows up with only Ubuntu options. No Windows. 

Anyone know how to fix this?[/QUOTE]

Well.............there are some "fixes".........do a repair of Vista and have Grub on a floppy. This will give you Vista back but, Grub will be gone, thus the need for a floppy with Grub on it to boot Ubuntu when you want. 

I've tried editing Grub and BCD/boot.mgr in Vista but neither has worked thus far. The new bootloader with Vista is so far not supported by anything but a program by Pro One will have it in its' next release. The name of the program is Vista Bootloader.

---

