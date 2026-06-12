---
title: "Sarge and Breezy..not using correct partition"
date: 2005-11-26
forum: Installation &amp; Upgrades
---

### Post by eldrich_rebello on 2005-11-26
this is another guys problem...but please help him out

Hi,
I reinstalled win XP and lost sarge 3.1.after reinstall partition order changed as below.partition tables rearranged...
first sarge was on /dev/sda7 now changed to /dev/sda8.swap earlier at sda6 is now at sda7....i restored the grub,edited fstab,mtab for sarge accordingly:
here's the panic message
Quote:
scsi0 :ata_piix
ATA: abnormal status 0x7F on port 0xE007
ata2 : disabling port
scsi1 :ata_piix
Vendor:ATA Model:ST380013AS Rev:3.18
Type: Direct-Access ANSI scsi revision:05
ide:Assuming 33Mhz system bus speed for PIO modes;override with idebus=xx
scsi device sda:156301488 512-byte hdwr sectors (80026 MB)
scsi device sda:drive cace:write back
scsi device sda:156301488 512-byte hdwr sectors (80026 MB)
scsi device sda:drive cace:write back
sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 sda11 > sda3
Attached scsi disk sda at scsi0,channel0,id0,lan0
VFS:Can't find ext3 filesystem on dev sda7.
mount:wrong fs type,bad option,bad superblock on /dev/sda7,
missing code page or other error
In some cases useful info is found in syslog -try
dmesg |tail or so.
Switching root ...
/usr/lib/yaird/exec/run_init ; current directory on the same filesystem as root:Success
kernel panic -not syncing:Attempted to kill
init!

as you can see the kernel is searching for ext3 on /dev/sda7 while sda8 now contains sarge and sda7 is swap
Also my /etc/fstab
Code:

root@ubuntu:/home/prakash# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         625     5020281    7  HPFS/NTFS
/dev/sda2             626        6269    45335430    f  W95 Ext'd (LBA)
/dev/sda5             626        1221     4787338+   b  W95 FAT32
/dev/sda6            1222        1532     2498076    b  W95 FAT32
/dev/sda7            1533        1666     1076323+  82  Linux swap / Solaris
/dev/sda8   *        1667        3003    10739421   83  Linux
/dev/sda9            3004        4567    12562798+   b  W95 FAT32
/dev/sda10           4568        5600     8297541   83  Linux
/dev/sda11           5601        6269     5373711   83  Linux

Code:
root@ubuntu:~# vi /mnt/debian/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda7       none            swap    swap            0       0
/dev/hda        /media/cdrom0   iso9660 ro,user,noauto  0       0
/dev/hdb        /media/cdrom1   iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/sda1       /mnt/win_C      ntfs    defaults        0       0 r0
/dev/sda3       /mnt/suse      reiserfs defaults        0       0
/dev/sda5       /mnt/win_D      vfat    defaults        0       0
/dev/sda6       /mnt/win_E      vfat    defaults        0       0
/dev/sda9       /mnt/rhel       ext3    defaults        0       0
/dev/sda10      /mnt/win_F      vfat    defaults        0       0
/dev/sda11      /mnt/ubuntu     ext3    defaults        0       0

devpts               /dev/pts             devpts     mode=0620,gid=5       0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0

---

### Post by bwog on 2005-11-26
Perhaps you can do a 'fake' installation of ubuntu: follow install till it gets to manual partitioning, mount the partitions for ubuntu breezy only (leave files on  disk, do not format partitions except swap). Install will stop because it detects a previous install. Now you can write grub to the hard disk again. (You did not mount windows, but ubuntu will detect it). 

I am not sure if this applies here or if there are simpler ways to restore. Point is: in this way ubuntu gets the right partitions, because you mount them.

---

### Post by metoo on 2005-11-26
You edited mtab? Isn't it updated automatically by the system? I never do anything with mtab. Well, as long as it is still writable...

You restored grub? Do you mean you edited /boot/grub/menu.lst ?
The kernel line in the sarge entry should point to /dev/sda8 .

---

### Post by deepclutch on 2005-11-26
Hai,
eldrich_rebello posted for my problem with sarge .thanks eldrich_rebello...will see in pcq forums....
@metoo
I set grub manually by mounting sarge chrooted with a fedora cd in rescue mode..as 
grub>root (hd0,7)
grub>setup (hd0,7)
now i think grub is installed in /boot partn,while MBR is left..
i edited grub to point each and every varbles to correct value;edited /etc/fstab
to /dev/sda8 as new root...i edited mtab too :confused: as this:
```
root@ubuntu:/home/prakash# vi /mnt/debian/etc/mtab
/dev/sda8 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0 
```
is there any other configuration files influencing kernel with correct filesystem..Please help Thank u very much....

---

### Post by deepclutch on 2005-12-03
anyone can help me?

---

