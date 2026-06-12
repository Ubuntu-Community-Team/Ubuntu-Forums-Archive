---
title: "Grub issue after Fresh install"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by xboxer21 on 2007-04-17
I installed Fiesta beta on my desktop and ran into a Grub issue immediately after install. Here is a brief description of what I did.
Setup: 2 drives
SATA (Primary SATA drive) 40Gigs (/dev/sda)
IDE (Slave Drive) 200Gigs (/dev/hda)
During installation I manually partitioned the drives
Here is the partition setup
/dev/sda1 35Gigs ext3 bootable  /
/dev/sda2 5 gigs                          swap
/dev/hda5 XFS not bootable        /home


after installation I removed the CD and rebooted the PC. When it rebooted It was stuck with a Sigma symbol and a flashing cursor. It will keep flashing the cursor until I hit the enter key. After hitting the enter key i see  the grub messages and the system boots up correctly. How can I have the system boot up by itself. Is anything wrong with my setup. Also I have setup the SATA drive as my 1st bootable drive.

Thanks

---

### Post by xboxer21 on 2007-04-18
I guess the problem was with the way I installed, Grub was installed on the IDE, I reinstalled with out the IDE and then after successful installation, I added the second drive.

---

