---
title: "Grub doesn't see linux partition on sata drive"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by alexxx1980 on 2008-06-24
Hi!

I'm trying to install ubuntu on my laptop dell inspiron 1525 with sata disk. Disk has 4 partitions:
1. HFS+ (Mac OS X Leopard)
2. Ext3 (Ubuntu)
3. NTFS (Win XP)
4. Fat32 (free)

If I check install bootloader while installing ubuntu (it doesn't matter into hd0 or sda2) I get error on 94% because bootloader could not be installed. Because of this issue I install ubuntu without bootloader and now I'm using live cd to install grub. I didn't create dedicated /boot partition. 

grub-install shows me the error "/boot/grub/stage1 not read correctly".

> ubuntu@ubuntu:/$ sudo grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:/$ sudo grub-install /dev/sda2
Could not find device for /boot: Not found or not a block device.

ubuntu@ubuntu:/$ mount -t ext3 /dev/sda2 /mnt
mount: only root can do that
ubuntu@ubuntu:/$ sudo mount -t ext3 /dev/sda2 /mnt
ubuntu@ubuntu:/$ sudo grub-install --root-directory=/mnt /dev/sda
The file /mnt/boot/grub/stage1 not read correctly.
ubuntu@ubuntu:/$ sudo grub-install --root-directory=/mnt /dev/sda2
The file /mnt/boot/grub/stage1 not read correctly.


ubuntu@ubuntu:/$ sudo grub-install --recheck --root-directory=/mnt /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
The file /mnt/boot/grub/stage1 not read correctly. 

And if I'm trying to use grub directly

> grub> geometry (hd0)
drive 0x80: C/H/S = 14593/255/63, The number of sectors = 234441648, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0xaf
   Partition num: 1,  Filesystem type unknown, partition type 0xb
   Partition num: 2,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type is fat, partition type 0xb

grub> root (hd0,1)

grub> setup

Error 11: Unrecognized device string

grub> 



grub> find /boot/grub/stage1

Error 15: File not found

grub> find /grub/stage1

Error 15: File not found

grub> 


grub> cat (hd0,4)/
 Possible files are: ._.Trashes .Trashes .Spotlight-V100 windowxp.tib 

grub> cat (hd0,2)/
Error 17: Cannot mount selected partition

grub> cat (hd0,1)/
Error 17: Cannot mount selected partition

grub> cat (hd0,1)/ 

Grub can't see any filesystems other than fat32. Could it be because of first HFS+ partition ?

fdisk shows:

> 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10521052

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2628    21102592   af  Unknown
/dev/sda2            2628        3933    10485760    b  W95 FAT32
/dev/sda3   *        3933        7849    31457280    7  HPFS/NTFS
/dev/sda4            7849       14594    54175123+   5  Extended
/dev/sda5            7849       14594    54175117+   b  W95 FAT32 


My mtab and fstab files

> ubuntu@ubuntu:/$ cat /etc/mtab
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
tmpfs /lib/modules/2.6.24-16-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/modules/2.6.24-16-generic/volatile tmpfs rw,mode=0755 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ubuntu 0 0
/dev/sda2 /mnt ext3 rw 0 0
ubuntu@ubuntu:/$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0 

My device.map file

> ubuntu@ubuntu:/mnt/boot/grub$ cat device.map
(fd0)	/dev/fd0
(hd0)	/dev/sda 

Contents of grub directory

> ubuntu@ubuntu:/mnt/boot/grub$ ls
default     e2fs_stage1_5  jfs_stage1_5    reiserfs_stage1_5  stage2
device.map  fat_stage1_5   minix_stage1_5  stage1             xfs_stage1_5 

---

