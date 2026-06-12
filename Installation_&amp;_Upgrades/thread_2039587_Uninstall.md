---
title: "Uninstall"
date: 2012-08-09
forum: Installation &amp; Upgrades
---

### Post by UselessMan on 2012-08-09
I have Ubuntu Dual Booted with Windows 7, how do I uninstall Ubuntu without destroying/reinstalling my windows?

---

### Post by Kalanac on 2012-08-09
Delete the Ubuntu partition then resize your windows partition to take up all the space (if you're wanting to get rid of Ubuntu completely)

Use the windows partition manager to do this.  You might loose the bootloader if it wasn't installed on the MBR so get a program like BootRepair BEFORE you do this.

[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

Also back up any windows files that are irreplaceable before resizing the partition, on rare occasions, things can go wrong.

---

### Post by Bliepo32 on 2012-08-09
Just uninstall it. Next, use GPARTED live cd to delete linux partitions and resize windows partition to fill the disc. Then download the supergrub disc (the legacy one, not grub 2!) and use the option WIN + MBR to fix your MBR.

---

### Post by UselessMan on 2012-08-09
But what if it removes the loader at the start with the menu to pick the OS you want, will it auto boot into windows?

---

### Post by Kalanac on 2012-08-09
No, you need to restore windows boot loader in the manner described above.

---

