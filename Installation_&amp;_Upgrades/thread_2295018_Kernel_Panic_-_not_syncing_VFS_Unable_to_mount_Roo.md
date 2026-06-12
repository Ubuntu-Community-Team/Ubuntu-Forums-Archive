---
title: "Kernel Panic - not syncing: VFS Unable to mount Root is on unknown-block(0,0)"
date: 2015-09-15
forum: Installation &amp; Upgrades
---

### Post by OriginalFlavor on 2015-09-15
I received a Kernel Panic error after updating Ubuntu server. 
*Note* I use the server to host a mediawiki.  The data is not backed up. I do not want to lose that data.


After passing the GRUB menu, I received the following error.

```
Kernel Panic - not syncing: VFS Unable to mount Root is on unknown-block(0,0)
CPU: 0 PID: 1 Comm: swapper/0 Not tainted 3.13.0-62-generic #102~precise1-Ubuntu
Hardware name: Dell Computer Corporation OptiPlex GX260 /OptiPlex GX260  , BIOS A)@ 07/25/2002
00000000 00000000 df437ec8 c16886a4 df437f14 df437eec c167d9da c187a7c4
c1b06c20 00000004 8eafa96c df437f14 fffffffa df72b000 df437f44 c1a0af88
c1868994 df437f14 df437f14 fffffffa 00000000 dfe5f560 c1868358 df72b000
```

I ran boot repair.  It completed "successfully" but after rebooting I received the same error.  The log can be found at [URL="http://paste.ubuntu.com/12299996/"]http://paste.ubuntu.com/12299996/
[/URL]
I tried to apply the fix in from [askubuntu post 41930]("http://askubuntu.com/feeds/question/41930") and had the following problems.

```
sudo fdisk -l
Disk /dev/loop0: 628.7 MiB, 659222528 bytes, 1287544 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 18.7 GiB, 20020396032 bytes, 39102336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000cca65

Device     Boot  Start      End  Sectors  Size Id Type
/dev/sda1  *      2048   499711   497664  243M 83 Linux
/dev/sda2       501758 39100415 38598658 18.4G  5 Extended
/dev/sda5       501760 39100415 38598656 18.4G 8e Linux LVM

Disk /dev/mapper/LDPubuntu--vg-root: 17.9 GiB, 19222495232 bytes, 37543936 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/mapper/LDPubuntu--vg-swap_1: 512 MiB, 536870912 bytes, 1048576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sdb: 3.7 GiB, 3942645760 bytes, 7700480 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x1f80e0a4

Device     Boot Start     End Sectors  Size Id Type
/dev/sdb1  *     2048 7700479 7698432  3.7G  b W95 FAT32

Disk /dev/zram0: 246.5 MiB, 258420736 bytes, 63091 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
```

Then the problems with the proposed solution started.  *Note *I used an LUBUNTU boot disk.  The system is old and only has a cd drive and even the updated BIOS will not allow to boot from USB...

```
lubuntu@lubuntu:~$ sudo mount /dev/sda1 /mnt
lubuntu@lubuntu:~$ sudo mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
lubuntu@lubuntu:~$ sudo mount --bind /proc /mnt/proc
mount: mount point /mnt/proc does not exist
lubuntu@lubuntu:~$ sudo mount --bind /sys /mnt/sys
mount: mount point /mnt/sys does not exist
lubuntu@lubuntu:~$ sudo mount --bind /run /mnt/run
mount: mount point /mnt/run does not exist
lubuntu@lubuntu:~$ sudo chroot /mnt
chroot: failed to run command ‘/bin/bash’: No such file or directory
lubuntu@lubuntu:~$ dpkg --list | grep linux-image
ii  linux-image-3.19.0-15-generic        3.19.0-15.15                        i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-15-generic  3.19.0-15.15                        i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-generic                  3.19.0.15.14                        i386         Generic Linux kernel image
```

what should I try next?
What information do I need to gather?

---

### Post by OriginalFlavor on 2015-09-23
I solved the issue by creating hard disk space on my boot partition by deleting previous version kernels.

I reviewed the install log more closely and realized that the install of the new version 14.04 LTS server failed because the drive had insufficient space.
This did not make much sense to me.  While I was using a small HDD, it should have had plenty of space for my data plus the new install.
So what was consuming the space?
I learned that ubuntu server keeps (i.e. does not delete) previously installed kernels by default for the purpose of rescuing failed systems.
From GRUB, I checked and realized I had ~8 kernels saved.
From GRUB, I deleted all but the most recent kernel.
The upgrade completed without issue on the now more empty partition.

---

