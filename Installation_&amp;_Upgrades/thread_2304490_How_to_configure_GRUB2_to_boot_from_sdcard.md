---
title: "How to configure GRUB2 to boot from sdcard"
date: 2015-11-27
forum: Installation &amp; Upgrades
---

### Post by Mattia_Adducchio on 2015-11-27
Hi,

I have a Intel Compute Stick Ubuntu Version and I have installed on external sdcard (mmcblk1) xubuntu 14.04.
 Now I want be able to start xubuntu from grub2 installed in mmcblk0.

**Bios not supports boot from sdcard.**

I haven't find a clear tutorial, please help me.

---

### Post by yancek on 2015-11-27
Not enough information.  You mention Ubuntu and Xubuntu so do you have Ubuntu installed on an internal drive and Xubuntu on the SSD?  Or do you just have Xubuntu on the SSD?  Where did you install the Grub bootloader for Xubuntu?  If you installed Grub2 for Xubuntu to the MBR of the SSD, you should be able to select it to boot in the BIOS by changing the boot priority.  If you do have Ubuntu on an internal drive, you could just boot it and run:  sudo update-grub.

---

### Post by grahammechanical on 2015-11-27
What hardware are you doing this on? And this is the blocker, as far as I can see:

> **Bios not supports boot from sdcard.**

Regards.

---

### Post by Mattia_Adducchio on 2015-11-27
Hi have Ubuntu on internal drive, Xubuntu on SSD and the bootloader is on internal driver. 
By the way I resolve my issue running boot-repair from live cd and selecting Xubuntu as default so.

---

