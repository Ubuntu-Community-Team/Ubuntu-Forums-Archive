---
title: "Fresh install - grub does not start"
date: 2011-11-10
forum: Installation &amp; Upgrades
---

### Post by W. Irving on 2011-11-10
Just installed a minimal Lucid x86 on a USB stick (Sandisk), but Ubuntu won't boot. It freezes at "Searching for Boot Record from USB RMD-FDD..OK". Pressing shift at boot does not bring up the grub menu.
The installation media was an identical USB stick containing the minimal image, and I've successfully booted the Lucid Live image on the same USB stick.

fdisk:
```
Disk /dev/sdc: 2001 MB, 2001076224 bytes
62 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00054899

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1016     1952721   83  Linux
```

There is no /var/log/syslog. /var/log/boot does exist, but contains "(Nothing has been logged yet.)" and was modified at install.

How do I troubleshoot this? :confused:

---

### Post by critin on 2011-11-10
I usually first assume a bad install, and then possibly a bad download--repeat both before I start to worry.   :P

---

### Post by W. Irving on 2011-11-11
> **critin said:**
> I usually first assume a bad install, and then possibly a bad download--repeat both before I start to worry.   :P

Let's assume it's not a bad install. I had an idea that the motherboard was unable to boot from ext partitions, so moved boot folder to FAT partition in beginning of memory and reinstalled grub. No luck.

Downloaded Super Grub Disk, dd'ed the ISO to a USB stick, and booted. Same thing: "Searching for Boot Record from USB RMD-FDD..OK" and halt. Downloaded Rescatux and tried running it, outcome no different.

This makes no sense at all.

---

### Post by W. Irving on 2011-11-11
I give up.
Writing the Super Grub Disk to a CD and booting off it using a IDE drive works.
According to [http://lists.gnu.org/archive/html/grub-devel/2010-09/msg00174.html](http://lists.gnu.org/archive/html/grub-devel/2010-09/msg00174.html) there could be a problem with the BIOS of the motherboard (Asrock K7S41GX) which could be circumvented by placing boot on a FAT 16 partition. Tried that too, with the same results. Not tried patching. Giving up and buying a IDE-SD adapter.

---

