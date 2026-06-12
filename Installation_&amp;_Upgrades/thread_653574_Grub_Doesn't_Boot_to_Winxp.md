---
title: "Grub Doesn't Boot to Winxp"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by Belfagor on 2007-12-30
hi! i' ve just installed hardy alpha2 and saw that it didn' t find my winxp...
here is the "cat /etc/mtab" result
--------------------------------------------------------------------
belfagor@belfagor:~$ cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-2-generic/volatile tmpfs rw 0 0
/dev/hda3 /media/hda3 vfat rw,utf8,umask=007,gid=46 0 0
/dev/hdb1 /media/hdb1 vfat rw,utf8,umask=007,gid=46 0 0
/dev/hdb5 /media/hdb5 vfat rw,utf8,umask=007,gid=46 0 0
/dev/hdb6 /media/hdb6 vfat rw,utf8,umask=007,gid=46 0 0
/dev/hdb7 /media/hdb7 vfat rw,utf8,umask=007,gid=46 0 0
/dev/sda1 /media/sda1 vfat rw,utf8,umask=007,gid=46 0 0
/dev/sda2 /media/sda2 vfat rw,utf8,umask=007,gid=46 0 0
/dev/sda3 /media/sda3 vfat rw,utf8,umask=007,gid=46 0 0
securityfs /sys/kernel/security securityfs rw 0 0
----------------------------------------------------------------------------------------------
and the "sudo fdisk -l" result
---------------------------------------------------------------------------------------------
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e7d1e7c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1898    15245653+  83  Linux
/dev/hda2            1899        1959      489982+   5  Extended
/dev/hda3   *        1960        4865    23342413+   c  W95 FAT32 (LBA)
/dev/hda5            1899        1959      489951   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a4e9f9b

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1390    11165143+   c  W95 FAT32 (LBA)
/dev/hdb2            1391        9729    66983017+   f  W95 Ext'd (LBA)
/dev/hdb5            1391        2922    12305758+   b  W95 FAT32
/dev/hdb6            2923        5793    23061276    b  W95 FAT32
/dev/hdb7            5794        9729    31615888+   b  W95 FAT32

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00053b5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10199    81923436    b  W95 FAT32
/dev/sda2           10200       20398    81923467+   b  W95 FAT32
/dev/sda3           20399       30401    80349097+   b  W95 FAT32
----------------------------------------------------------------------------------------------


please help me! thanks from now on

---

### Post by taseedorf on 2007-12-30
Try adding this code to your grub menu.lst file in /boot/grub near the bottom where it shows your Ubuntu boot scripts
where hdZZ is where your xp partition is,than change the (hdZ,Z) to show what disk XP is on and than what partition such as ... (hd0,1)
the other options at the bottom can be changed depending on what your preferences are

on /dev/hdZZ   
title		Windows Xp  
root		(hdZ,Z)
savedefault
makeactive
chainloader	+1

See if that helps?
I am a new user as well, but you can certainly try this and I believe it may work.
make sure to back up menu.lst though.

---

