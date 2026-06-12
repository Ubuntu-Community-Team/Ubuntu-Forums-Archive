---
title: "Grub rescue and no partition table"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by NikitaUtiu on 2010-09-01
I normally shut my computer down and started it later, but it got into grub rescue. I couldn't get to start ubuntu with grub rescue. I put the live cd in and look at gparted. Gpartede says that my hard disk isn't partitioned and I get this error: 
Invalid partition table on /dev/sda -- wrong signature on 7061

I want to save my data. I have Ubuntu 10.04 installed. Is there any way to salvage it ?

Sincerely, NikitaUtiu.

---

### Post by lukeiamyourfather on 2010-09-01
Did you do anything with the disk unusual before the issues like resize partitions? The disk might have failed or is in the process of failing. Hopefully you have a backup of important data.

---

### Post by srs5694 on 2010-09-01
Post the output of the command "sudo fdisk -lu /dev/sda" when typed from an emergency boot CD. (You may need to delete the "sudo" part on some emergency discs.)

It's conceivable that the disk is not very badly damaged, in which case there may be a relatively simple recovery procedure. OTOH, if the partition table is completely trashed, you may need to use [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) to recover your partitions. In a worst-case scenario, your disk's contents have been completely overwritten or corrupted, in which case I hope you've got good backups.

---

### Post by NikitaUtiu on 2010-09-02
Nevermind, recovered the partition table with gpart and reinstalled grub from live CD. Apparently, it happened because I failed to mirror a harddisk with netcat.:lolflag:

---

