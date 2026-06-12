---
title: "Second hard drive not in fdisk after upgrade"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by rex_the_first on 2007-04-22
Hi, I just upgraded from Edgy to Feisty and I cannot find my second hard drive with fdisk.

When I load up Feisty the loading bar hangs for a while then it loads ok.  I noticed that my second hard drive was missing.  I tried 

> sudo fdisk -l

and I get

> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3305    26547381    7  HPFS/NTFS
/dev/hda2            3306        9541    50090670   83  Linux
/dev/hda3            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris


and nothing else.  My 250GB serial ATA  hard drive does not seem to show up but worked fine in Edgy!  It is on IDE Channel 4 (I think) and was sda1 but I cannot find it in Feisty.  When I load up windows it can find my second hard drive.

Not sure if it is important but 
/etc/fstab
had the wrong UUID for my swap but all the other UUID's were correct.

Thank you very much in advance!

P.S.
This seems to be a similar problem to  [amartani 's post]("http://ubuntuforums.org/showthread.php?t=419201")

---

### Post by rex_the_first on 2007-04-22
Oh, and if you don't know how to solve this, does anyone know how to uninstall Feisty?

---

### Post by rex_the_first on 2007-04-23
I have searched the forum still and cannot find a solution so bump

---

### Post by solarix on 2007-04-23
Have you tried to use Testdisk ?

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

Burn it on a CD-RW and take a look maybe there is a partition table damaged.

---

### Post by Blur-king on 2007-04-23
Hi you will need to re mount it. Use gparted to locate it . The following has a good tutorial on this thanks to psychocats . [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)  cherio

---

### Post by rex_the_first on 2007-04-23
Thanks but the hard drive is still not showing up.  Ubuntu cannot see it at all, it cannot find the drive to mount.  In gparted and Testdisk the dive is not visible but it IS there in windows.  This makes me think that the new uses of SCSI drivers for serial ATA drives might be flawed.

---

### Post by rex_the_first on 2007-04-24
Sorry to have to bump my post again but I am really stuck.  Ubuntu does not recognise my USB pen and losing a hard drive is a real pain.  I am downloading Edgy now but I really hope not to have to install it.

---

