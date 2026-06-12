---
title: "Grub : Error 17"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by Mattt on 2008-07-29
I have searched for this, really I'm not lazy, I just have not found a solution.

Starting with a XP/Vista pc, I installed Ubuntu on a separate drive.   Everything went swimmingly well until the final reboot.

On restarting, if I pick Ubuntu I get Error 17.
If I pick Vista I get a different error about an invalid executable.

After reading a heap of threads on these forums, I booted from Live Cd and extracted the following information.

Firstly, my disks are setup in BIOS as follows.

[FONT="Courier New"]IDE0 : Not used
IDE1 : Not Used
First SATA  : 500mb data
Second SATA : 160GB new Ubuntu install
Third SATA  : 200GB XP on one partition, Vista on another.
Fourth SATA : DVD/CDROM[/FONT]


FDISK (included two USB sticks which happen to be plugged in.)

[FONT="Courier New"]ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x147d75ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976771119   488385528+  42  SFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xae87bf69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   299805029   149902483+  83  Linux
/dev/sdb2       299805030   312576704     6385837+   5  Extended
/dev/sdb5       299805093   312576704     6385806   82  Linux swap / Solaris

Disk /dev/sdc: 200    .0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdb14db14

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   204796619   102398278+   7  HPFS/NTFS
/dev/sdc2       204797952   390717439    92959744    7  HPFS/NTFS

Disk /dev/sdd: 129 MB, 129761280 bytes
4 heads, 62 sectors/track, 1021 cylinders, total 253440 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdh: 506 MB, 506986496 bytes
16 heads, 61 sectors/track, 1014 cylinders, total 990208 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1              61      989663      494801+   b  W95 FAT32
[/FONT]


The device.map : 

[FONT="Courier New"]Device Map
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd
(hd4)    /dev/sdh [/FONT]


Menu.lst
[FONT="Courier New"]
title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=2ef409ec-3401-4159-a090-206e489d25e3 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=2ef409ec-3401-4159-a090-206e489d25e3 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Windows Vista/Longhorn (loader)
root        (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1
[/FONT]


Every thing look good to me.
The bios, fdisk and device map all seem aligned and grub references the right drives.

Any ideas ?

---

### Post by xen-uno on 2008-07-29
This may help ...

[http://ubuntuforums.org/showpost.php?p=3518911&postcount=9](http://ubuntuforums.org/showpost.php?p=3518911&postcount=9)

---

### Post by Mattt on 2008-07-29
Thanks but doesn't that post refer to situation where the devices are wrongly detected?
I think mine are detected properly?

Have I understood the device.map properly ?


**BIOS **First SATA : 500mb data
**fdisk **/dev/sda: 500.1 GB
**device.map** (hd0) /dev/sda

**BIOS **Second SATA : 160GB new Ubuntu install
**fdisk **/dev/sdb: 160.0 GB
**device.map** (hd1) /dev/sdb
**menu **root (hd1,0) Ubuntu 8.04.1, kernel 2.6.24-19-generic

**BIOS **Third SATA : 200GB XP on one partition, Vista on another.
**fdisk **/dev/sdc: 200 .0 GB
**device.map** (hd2) /dev/sdc
**menu** root (hd2,0) Windows Vista/Longhorn (loader)

---

### Post by xen-uno on 2008-07-29
Looks fine to me ... that's a head scratcher. I had a type 42 SFS show up on my 160 GB drive. SFS, I'm guessing, stands for Simple File System ... maybe? Mine was formatted as an NTFS originally, but there is a possibility that Ubuntu doesn't like that drive type (can't prove it). XP x64's Disk Management wouldn't let me change the 160 to an extended partition and turn it into one big logical drive, so I used Paragon's Hard Disk Manager to make it extended first off, then logical (maybe), then used XP to format (maybe to define as logical as well). As you know, you will have to copy the drive contents off somewhere. I not positive it helped, cause I made a host of other changes in a quest to get auto-mount to work correctly ... however, my gut feeling is that it did.


BTW: Great grub page here ... very deep > [http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by Mattt on 2008-07-29
That's interesting, the SFS partition is an xp formatted, dynamic partition.  I could not change it back to simple.  not with out trashing it.

I might pull that drive and regig the HDn numbers and such.

thanks

---

### Post by xen-uno on 2008-07-29
Aye ... SFS = Secure File System

42 can mean a few things ...

42 Linux swap (sharing disk with DRDOS)

42 SFS (Secure Filesystem) SFS is an encrypted filesystem driver for DOS on 386+ PCs, written by Peter Gutmann.

42 Windows 2000 dynamic extended partition marker

    If a partition table entry of type 0x42 is present in the legacy partition table, then W2K ignores the legacy partition table and uses a proprietary partition table and a proprietary partitioning scheme (LDM or DDM). As the Microsoft KnowledgeBase writes: Pure dynamic disks (those not containing any hard-linked partitions) have only a single partition table entry (type 42) to define the entire disk. Dynamic disks store their volume configuration in a database located in a 1-MB private region at the end of each dynamic disk.

... from [http://www.win.tue.nl/~aeb/partitions/partition_types-1.html](http://www.win.tue.nl/~aeb/partitions/partition_types-1.html)

Changing from 42 to 7 here ... [http://osdir.com/ml/file-systems.ntfs.devel/2004-09/msg00033.html](http://osdir.com/ml/file-systems.ntfs.devel/2004-09/msg00033.html)

---

