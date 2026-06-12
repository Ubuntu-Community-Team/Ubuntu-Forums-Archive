---
title: "Switch from grub in MBR to using it from sda3"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by b166er on 2008-11-26
Hi
I have two installations of grub, one Is configured the way I want it, and one is not working.

The problem is that no matter witch partition I mark with the Boot-flag my system will always boot from grub that is installed in the Mbr.

Can I uninstall the grub thats inside my MBR so I would start to boot from Sda3 (the one marked with the boot-flag)?

---

### Post by lemming465 on 2008-11-28
Unlike windows, grub doesn't use the boot/active flag to pick where stuff is loaded from.  What you want to do is boot the partition you like, and run ```
sudo grub-install /dev/sda
``` to overwrite the MBR with a revised version pointing at your favorite /boot directory and menu.

---

### Post by GROMS on 2008-11-29
I've got a slightly different problem but directly relates.
 My system has a 3ware SATA controller and 4 drives using Raid 1. After installation, the only way I can boot the system is to have it boot from the CD. Even after changing the Bios to boot from the HD otherwise I get a message to the effect that there is no system disk. From the install CD I get the menu to: Install, check memory, ck CD and "Boot from first hard drive" - when picked system boots from installed 8.04 Hardy 64 code. Attached are results from Fdisk and lshw command.

```
From fdisk:
Disk /dev/sda: 499.9 GB, 499989348352 bytes
255 heads, 63 sectors/track, 60786 cylinders, total 976541696 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003eab6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   936942929   468471433+  83  Linux
/dev/sda2       936942930   976527089    19792080    5  Extended
/dev/sda5       936942993   976527089    19792048+  82  Linux swap / Solaris

Disk /dev/sdb: 499.9 GB, 499989348352 bytes
255 heads, 63 sectors/track, 60786 cylinders, total 976541696 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00058f7f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976527089   488263513+  83  Linux

----------------------------------------------------------------

sudo dd for sda

e@linux-64:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 ff00                                   
0000002

-------------------------------------
gksudo gedit /boot/grub/menu.1st
  opened a blank file edit window

--------------------------
sudo partman
  first returned error of no OS
  second time gave window showing at top "Package configuration" and then a sub window titled "Starting up the partitioner" and a progress bar showing a red 57% marker then seems to freeze. Finally just closed window.

----------------------------
in file system /boot/grub/device.map shows:

(hd0)	/dev/sda
(hd1)	/dev/sdb
---------------------------------
in dev/disk/by-id
it shows the following files with pointers:
scsi-1AMCC_6QG0ZV63E9D3A100F5BA
scsi-1AMCC_6QG0ZV63E9D31A00F5BA-part1
scsi-1AMCC_6QG0ZV63E9D31A00F5BA-part2
scsi-1AMCC_6QG0ZV63E9D31A00F5BA-part5
scsi-1AMCC_6QG0ZV63E9D31A00A326
scsi-1AMCC_6QG0ZV63E9D31A00A326-part1
--------------------------------------
in file browser there is an entry for "File System" and one for "500.0 GB Media". when I clicked on the second it brought up a password request to mount. Did it. Opening it showed just a folder called "lost+found".
-------------------------------------
 
from lshw:

id:	
ide:1
description: 	IDE interface
product: 	MCP55 SATA Controller
vendor: 	nVidia Corporation
physical id: 	
e
bus info: 	
pci@0000:00:0e.0
version: 	a2
width: 	32 bits
clock: 	66MHz
capabilities: 	ide pm msi ht bus_master cap_list
configuration:	
driver	=	sata_nv
latency	=	0
maxlatency	=	1
mingnt	=	3
module	=	sata_nv
id:	
ide:2
description: 	IDE interface
product: 	MCP55 SATA Controller
vendor: 	nVidia Corporation
physical id: 	
e.1
bus info: 	
pci@0000:00:0e.1
version: 	a2
width: 	32 bits
clock: 	66MHz
capabilities: 	ide pm msi ht bus_master cap_list
configuration:	
driver	=	sata_nv
latency	=	0
maxlatency	=	1
mingnt	=	3
module	=	sata_nv
id:	
ide:3
description: 	IDE interface
product: 	MCP55 SATA Controller
vendor: 	nVidia Corporation
physical id: 	
e.2
bus info: 	
pci@0000:00:0e.2
version: 	a2
width: 	32 bits
clock: 	66MHz
capabilities: 	ide pm msi ht bus_master cap_list
configuration:	
driver	=	sata_nv
latency	=	0
maxlatency	=	1
mingnt	=	3
module	=	sata_nv



id:	
pci:2
description: 	PCI bridge
product: 	MCP55 PCI Express bridge
vendor: 	nVidia Corporation
physical id: 	
13
bus info: 	
pci@0000:00:13.0
version: 	a2
width: 	32 bits
clock: 	33MHz
capabilities: 	pci pm msi ht pciexpress normal_decode bus_master cap_list
configuration:	
driver	=	pcieport-driver
id:	
storage
description: 	RAID bus controller
product: 	9650SE SATA-II RAID
vendor: 	3ware Inc
physical id: 	
0
bus info: 	
pci@0000:03:00.0
logical name: 	
scsi0
version: 	01
width: 	64 bits
clock: 	33MHz
capabilities: 	storage pm msi pciexpress bus_master cap_list emulated
configuration:	
driver	=	3w-9xxx
latency	=	0
module	=	3w_9xxx
id:	
disk:0
description: 	SCSI Disk
product: 	9650SE-4LP DISK
vendor: 	AMCC
physical id: 	
0.0.0
bus info: 	
scsi@0:0.0.0
logical name: 	
/dev/sda
version: 	3.08
serial: 	6QG0ZV63E9D3A100F5BA
size: 	465GiB (499GB)
capabilities: 	partitioned partitioned:dos
configuration:	
ansiversion	=	5
signature	=	0003eab6
id:	
volume:0
description: 	EXT3 volume
vendor: 	Linux
physical id: 	
1
bus info: 	
scsi@0:0.0.0,1
logical name: 	
/dev/sda1
logical name: 	
/
logical name: 	
/dev/.static/dev
version: 	1.0
serial: 	45578908-cb3b-4943-9bdd-99fb1bb00968
size: 	446GiB
capacity: 	446GiB
capabilities: 	primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
configuration:	
created	=	2008-10-11 10:53:20
filesystem	=	ext3
modified	=	2008-11-11 09:06:45
mount.fstype	=	ext3
mount.options	=	rw,relatime,errors=remount-ro,data=ordered
mounted	=	2008-11-11 09:06:45
state	=	mounted
id:	
volume:1
description: 	Extended partition
physical id: 	
2
bus info: 	
scsi@0:0.0.0,2
logical name: 	
/dev/sda2
size: 	18GiB
capacity: 	18GiB
capabilities: 	primary extended partitioned partitioned:extended
id:	
logicalvolume
description: 	Linux swap / Solaris partition
physical id: 	
5
logical name: 	
/dev/sda5
capacity: 	18GiB
capabilities: 	nofs
id:	
disk:1
description: 	SCSI Disk
product: 	9650SE-4LP DISK
vendor: 	AMCC
physical id: 	
0.1.0
bus info: 	
scsi@0:0.1.0
logical name: 	
/dev/sdb
version: 	3.08
serial: 	6QG14BACE9D3A100A326
size: 	465GiB (499GB)
capabilities: 	partitioned partitioned:dos
configuration:	
ansiversion	=	5
signature	=	00058f7f
id:	
volume
description: 	EXT3 volume
vendor: 	Linux
physical id: 	
1
bus info: 	
scsi@0:0.1.0,1
logical name: 	
/dev/sdb1
version: 	1.0
serial: 	99bf96a7-d205-4a89-8f6a-18812af66398
size: 	465GiB
capacity: 	465GiB
capabilities: 	primary journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
configuration:	
created	=	2008-11-11 08:29:52
filesystem	=	ext3
modified	=	2008-11-11 08:31:34
state	=	clean

```

 Tried doing command hdparm -I /dev/sda and got "HDIO_DRIVE_CMD failed: invalid arguement". 
How do I get the system to boot from the hard disk??
(new to linux)
Stephen

---

### Post by lemming465 on 2008-11-29
> My system has a 3ware SATA controller and 4 drives using Raid 1
Meaning, no disk drives hooked up to the motherboard nVidia controller slots, 4 drives hooked to the 3ware, 3ware hardware mirrors two RAID-1 pairs.
> hdparm -I /dev/sda and got "HDIO_DRIVE_CMD failed: invalid arguement". 
This is normal for hardware RAID scenarios; hdparm isn't talking to a real disk, it's talking to an emulated fictional disk created by the RAID controller, and the emulated logical disk lacks some of the features of real physical disks.

I'm guessing you have a DVD drive hooked to the Nvidia controller, so you can't just disable the onboard controller entirely.  Though that is an experiment worth trying, to see if it affects the boot problem.  The boot problem is probably that the BIOS wants the first disk on the first controller, not just any old disk.  See if you have any BIOS options to disable disk boot off the nVidia, or to try the 3ware controller first.  Make sure any BIOS options for booting off the 3ware are enabled; it probably has a BIOS submenu where that is controlled.

---

### Post by GROMS on 2008-12-01
SOLVED! Contacted 3ware and got a hint. Somehow, the install went to unit 1 instead of unit 0 of the 4 drive array. Moved unit 1 up, reset MB bios and rebooted - IT WORKS (learn something new all the time.




The MB bios has boot order of (trying) HD, CD, removeable. Under Hard Disk Drives option it has only the 3ware controller listed. Where it shows the onboard sata controller - all are disabled. Trying to boot this way - goes through post, then installs 3ware bios - then clears screen and just sits ther. Looking t the system, it doesn't try to access either the CD drive or floppy (does not appear to access the HD's either). In the fdisk output showing sda, there is and entry /dev/sda1 under 'Device' and an '*' under 'Boot' with a starting point of 63.
If it is trying to access /boot/grub/menu.1st, this file is blank.

What would happen if Ijust tried a reinstall??****

---

