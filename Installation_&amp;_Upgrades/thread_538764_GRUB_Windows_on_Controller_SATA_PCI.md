---
title: "GRUB: Windows on Controller SATA PCI"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by Nydirac on 2007-08-30
Hi! I get this message trying to boot Windows: "Error 23 'Selected Disk Does Not Exist'" 

Current configuration:

The SATA HD is under a Controller SATA PCI ( based on VIA 6421A)

-------------------------------------------------------------------------------------------
fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        9963    59054940    f  W95 Ext'd (LBA)
/dev/sda5            2612        9963    59054908+   e  W95 FAT16 (LBA)

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          49      393561   83  Linux
/dev/hda2              50         547     4000185   82  Linux swap / Solaris
/dev/hda3             548        1792    10000462+  83  Linux
/dev/hda4            1793        4998    25752195   83  Linux

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
151 heads, 20 sectors/track, 106017 cylinders
Units = cilindri of 3020 * 512 = 1546240 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       99819   150726533+   7  HPFS/NTFS

-------------------------------------------------------------------------------------------

Device.map

(hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/sda


-------------------------------------------------------------------------------------------

menu.lst

## default num
default		0

## timeout sec
timeout		10

title		Ubuntu, kernel 2.6.20-16-386
root		(hd0,0)
kernel		/vmlinuz-2.6.20-16-386 root=UUID=54a558bf-7d0c-4d85-a245-1c1bcf10835b ro vga=794 quiet
initrd		/initrd.img-2.6.20-16-386
quiet
savedefault

title		Microsoft 2003 SERVER
rootnoverify	(hd2,0)
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader +1

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet


-------------------------------------------------------------------------------------------

blkid

/dev/hda1: UUID="75460812-9f18-4a90-a946-38dfe102c058" TYPE="ext2" 
/dev/hda2: UUID="16cefd10-3189-4a8f-9463-2d15235c0f70" TYPE="swap" 
/dev/hda3: UUID="54a558bf-7d0c-4d85-a245-1c1bcf10835b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda4: UUID="7e772eef-b70a-4637-9f0b-99d6b4bb3a3f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb1: TYPE="ntfs" 
/dev/sda1: TYPE="ntfs" 

Maybe GRUB can't find the HD on the controller? any ideas?


PS: Sorry for bad english ^^

---

### Post by Nydirac on 2007-08-30
up

---

