---
title: "&quot;Successful install&quot; results in &quot;Boot device not found&quot;"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by robinz on 2007-05-15
I've booted off the live v704 CD and installed the OS to a SCSI drive (IBM 18Gb) on a Mylex/BusLogic controller. The installation completes successfully and all is well until the first reboot to the hard disk. The boot fails with "Boot device not found".

I've told the motherboard (ASUS K8U-X) to boot first from SCSI. It appears that during the POST phase, I do not see the controller bios being displayed. It almost appears that the ASUS motherboard does not recognize the scsi controller. When I go back and boot off the live CD and go into the gnome partition editor, I see the disk is there with the boot flag set. I've included a 3 screen shots from the partition editor, device manager and the file browser. The results from the command "sudo fdisk -l" yield;

Disk /dev/sda: 18.3 GB, 18351959040 bytes
255 heads, 63 sectors/track, 2231 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2132    17125258+  83  Linux
/dev/sda2            2133        2231      795217+   5  Extended
/dev/sda5            2133        2231      795186   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Device Boot      Start         End      Blocks   Id  System


I am at a loss as to what to do next. Anyone have any idea's?

Robin

---

### Post by robinz on 2007-05-22
So much for the "glorious" support from the open source community.

Robin

---

