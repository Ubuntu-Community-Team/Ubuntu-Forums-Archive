---
title: "installation problem"
date: 2015-04-18
forum: Installation &amp; Upgrades
---

### Post by satimis on 2015-04-18
Hi all,

Ubuntu 14.04 on USB
SSD1 - 1TB
SSD2 - 120G
Motherboard - ASUS M5A97 Le R20


Something very strange happened here.  I tried to install Ubuntu on SSD1 first.  Both SSDs are connected and detected by BIOS.

Booting up the PC

.....
......
```
This computer current has no detected operating system.  What would you like to do?
```
(check) Erase disk and install Ubuntu
-> Continue

Select drive: [SCSI1(0,0,0)(sda - 1.0TB ATA TS1TSSD370]
(remark: other SSD also detected - SCSI1(0,0,0)(sdb - 128.0 GB ATA ADATA SX900)
-> Install Now

It pop back to following page again```

This computer current has no detected operating system.  What would you like to do?

```

I have tried an hour with the same result.  Choosing SSD2 couldn't solve the problem.

This USB stick has been run to install Ubuntu 14.04 in multiple times without problem.  Please help.  Whether it is not allowed connecting 2 SSDs in the PC at the same time?

Regards
satimis

---

### Post by grahammechanical on 2015-04-18
Is the installer giving an option to choose which drive to install Ubuntu on? Are you selecting sda = 1TB? If we do not make a selection then the installer has no choice but to ask again.

You may wish to avoid complications by disconnecting the drive that you do not want Ubuntu to be installed on. Just a thought.

Regards.

---

### Post by satimis on 2015-04-18
> **grahammechanical said:**
> Is the installer giving an option to choose which drive to install Ubuntu on? Are you selecting sda = 1TB? If we do not make a selection then the installer has no choice but to ask again.
Yes.  2 SSDs are available for selection.  I have tried selecting both with the same result.

> 
You may wish to avoid complications by disconnecting the drive that you do not want Ubuntu to be installed on. Just a thought.

I have tried following arrangement;
1) Installed SSD2 taking up entire disc without LVM and without SSD1 connected.  Then installed SSD1 with LVM selected also without SSD2 connected.  Plug in SSD2.  Both Ubuntu installed on SSD1 and SSD2 worked without problem.  I can select either of them on BIOS to boot.

2) Unplug SSD1 and reinstall SSD2 with LVM selected.  Then plug in SSD1 again.  I could only boot SSD1 via BIOS but SSD2 is detected on BIOS.  To boot SSD2 I must unplug SSD1

That is the present situation.  Ubuntu on both SSDs are still working

Regards
satimis

---

### Post by satimis on 2015-04-18
Hi all,

Further to my late posting

I suspect whether it is the problem of the motherboard.  This is a brand new PC built about one week.  This is also the second new motherboard (ASUS M5A97 Le R20) replaced by Asus agent.  The first motherboard could not boot PC.

Hard drives connection
SSD1 - connected to P1 SATA port
SSD2 - connected to P2 SATA port

I can install or reinstall Ubuntu without problem if only one SSD is connected.  If connecting 2 SSDs the BIOS detects them.  I couldn't select them to proceed as the situation mentioned on my original posting.

After installing Ubuntu on SSD separately and connencting them to the PC I could only boot SSD2 (SATA port P2).  The BIOS detects both SSDs but always boot SSD2 automatically even selecting to boot SSD1 (SATA port P1).  To boot SSD1 (SATA port P1) I must disconnect the cable of SSD2 (SATA port P2).

Besides the PC has been stopped working once.  Another problem it beeped three times.  I have to switch off the power and switch it on again to solve the problem.

I'll contact Asus agent here on Monday if I couldn't figure out the problem.

Regards
satimis

---

### Post by satimis on 2015-04-19
Hi all,

Performed following test:-

SSD1 (1TB) - SATA-1 port
SSD2 (120G) - SATA-2 port

1)
Disconnected SSD1.  Booted PC with USB to install Ubuntu 14.04 desktop on SSD2.  It went through without complaint.  After reboot Ubuntu 14.04 is now running on the SSD2 without problem.

2)
Reconnected SSD1, still with SSD2 connected.

Booted PC with USB to install Ubuntu 14.04 desktop on SSD1.  This time I was allowed to select drive (SSD1/SSD2).

Installation went through without complaint.  After reboot Ubuntu 14.04 is now also running on the SSD1 without problem.

On BIOS I can select either SSD to boot without problem.  Also I can mount SSD1/SSD2 to read its data after booting up the PC.

Conclusion:
I think the motherboard may not have problem.  It was because it is NOT allowed having 2 LVMs on ONE PC.

Now a remaining side-problem;
I have another HDD (WD 1.5TB) on LVM, only about 1/2 space occupied.  I couldn't mount it running either SSD. Is there any solution?  

I want to moving its data to SSD1, wiping out this HDD and moving the data back.  I'm prepared using this HDD for storage only.

Please help.  Thanks

Regards
satimis

---

### Post by dino99 on 2015-04-19
you should understand that all your issues are due to the fact that LVM is not used as it should to work properly

---

### Post by satimis on 2015-04-19
Hi all,

Problem solved as follows:-

On SSD2 run;

$ sudo apt-get install lvm2

$ su
# fdisk -l```


Disk /dev/sda: 1024.2 GB, 1024209543168 bytes
255 heads, 63 sectors/track, 124519 cylinders, total 2000409264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000933b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1933504511   966751232   83  Linux
/dev/sda2      1933506558  2000408575    33451009    5  Extended
/dev/sda5      1933506560  2000408575    33451008   82  Linux swap / Solaris

Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00061119

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   183164927    91581440   83  Linux
/dev/sdb2       183166974   250068991    33451009    5  Extended
/dev/sdb5       183166976   250068991    33451008   82  Linux swap / Solaris

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bf74f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048      499711      248832   8e  Linux LVM
/dev/sdc2          501758  2930276351  1464887297    5  Extended
/dev/sdc5          501760  2930276351  1464887296   8e  Linux LVM

Disk /dev/mapper/LVM1.5D-root: 300.0 GB, 299997593600 bytes
255 heads, 63 sectors/track, 36472 cylinders, total 585932800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/LVM1.5D-root doesn't contain a valid partition table

Disk /dev/mapper/LVM1.5D-swap: 4999 MB, 4999610368 bytes
255 heads, 63 sectors/track, 607 cylinders, total 9764864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/LVM1.5D-swap doesn't contain a valid partition table

Disk /dev/mapper/LVM1.5D-data: 1195.0 GB, 1195045289984 bytes
255 heads, 63 sectors/track, 145289 cylinders, total 2334072832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/LVM1.5D-data doesn't contain a valid partition table

```

# pvs```

  PV         VG      Fmt  Attr PSize   PFree  
  /dev/sdc1          lvm2 a--  243.00m 243.00m
  /dev/sdc5  LVM1.5D lvm2 a--    1.36t      0 

```

# vgchange -ay LVM1.5D```

  3 logical volume(s) in volume group "LVM1.5D" now active

```

Then on -> "Files" I can find HDD device.  Data on HDD can be copied with drag-n-drop.

Start SSD1 and repeated above steps.

Now data can be moved amongst SSD1, SSD2 and HDD.  I think it is NOT necessary making any change on the HDD.

Thanks

Regards
satimis

---

