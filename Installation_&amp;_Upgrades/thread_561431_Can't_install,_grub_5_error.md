---
title: "Can't install, grub 5 error"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by disk11 on 2007-09-27
I've been trying to do a clean install of Ubuntu for a day now, and I get nothing but error 5 in GRUB.  I've tried 7.04 ubuntu and 7.10 ubuntu beta to no avail.  I've also done manual and guided/auto partitioning and it still won't boot.

Here's the hardware setup:
Abit AI7
1 GB of RAM
P4 2.8B
IDE1: WD1200JB (install target)
IDE2: NEC 3550A DVD-DL RW
Promise Ultra 100 with 2x WD2500JBs on sperate channels

Something odd I have noticed is the WD1200JB is showing up as a SCSI drive, and in GRUB it is listed as hd (2,1).

---

### Post by logos34 on 2007-09-27
boot the ubuntu live cd. open a terminal and run

**sudo fdisk -l** (lowercase L)

post it.  

[http://users.bigpond.net.au/hermanzone/p15.htm#5_](http://users.bigpond.net.au/hermanzone/p15.htm#5_)

---

### Post by disk11 on 2007-10-01
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45df45de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         249     2000061   82  Linux swap / Solaris
/dev/sda2   *         250        3653    27342630   83  Linux
/dev/sda3            3654       14593    87875550   83  Linux

Disk /dev/hde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/hdg: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/hdg doesn't contain a valid partition table

```

---

### Post by logos34 on 2007-10-01
Ubuntu now uses the libata scsi driver to ID all disks, so it sees everything (including IDE) as scsi devices (/dev/sdx),  But it appears your pata raid controller threw it for a loop (hde, hdg).

Try this:

Reboot and at the grub menu screen, hit 'e' key on the first ubuntu kernel.  Hit 'e' again to edit the 'root' line.  Change from (hd2,1) to **(hd[COLOR="Red"]0[/COLOR],1)**.  Hit enter and 'b' to boot.  If it works go straight to menu.lst and correct the 'groot' and 'root' lines:
[B]
gksudo gedit /boot/grub/menu.lst[/B]

---

### Post by disk11 on 2007-10-01
"0,1" didn't work, but for some reason "1,1" did.  Thanks for the help.

---

