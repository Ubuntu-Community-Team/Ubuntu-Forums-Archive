---
title: "Dual Boot 2 Ubuntu Missing /boot"
date: 2013-05-21
forum: Installation &amp; Upgrades
---

### Post by fonsi2099 on 2013-05-21
dual boot 13.04 + 12.04  How can login in my first OS 13.04

I have deleted  my /boot partition of 13.04 and I have rewritten  it accidentally with/boot partition of 12.04 by re- installing 12.04, now I have two OS 13.04 and 2nd OS 12.04   but I have not  dual-boot  in grub menu  I see only 12.04 not choice for 13.04.  how can I log in  my partition of 13.04?
"
lts-Aspire-S3:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-30-generic
Found initrd image: /boot/initrd.img-3.5.0-30-generic
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found memtest86+ image: /memtest86+.bin
ERROR: sil: invalid metadata checksum in area 3 on /dev/sda
ERROR: sil: invalid metadata checksum in area 3 on /dev/sda
ERROR: sil: invalid metadata checksum in area 3 on /dev/sda
ERROR: sil: invalid metadata checksum in area 3 on /dev/sda
ERROR: sil: invalid metadata checksum in area 3 on /dev/sda
ERROR: sil: invalid metadata checksum in area 3 on /dev/sda
ERROR: sil: invalid metadata checksum in area 3 on /dev/sda
ERROR: sil: invalid metadata checksum in area 3 on /dev/sda
ERROR: sil: invalid metadata checksum in area 3 on /dev/sda
ERROR: sil: invalid metadata checksum in area 3 on /dev/sda
ERROR: sil: invalid metadata checksum in area 3 on /dev/sda
ERROR: sil: invalid metadata checksum in area 3 on /dev/sda
Found Ubuntu 13.04 (13.04) on /dev/sda2
done"

lts-Aspire-S3:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004ed07

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      976895      487424   83  Linux
/dev/sda2          976896    49805311    24414208   83  Linux
/dev/sda3        49807358   625141759   287667201    5  Extended
/dev/sda5        49807360   166991871    58592256   83  Linux
/dev/sda6       166993920   264648703    48827392   83  Linux
/dev/sda7       264650752   362305535    48827392   83  Linux
/dev/sda8       362307584   420903287    29297852   83  Linux
/dev/sda9       459964416   538087423    39061504   83  Linux
/dev/sda10      538089472   577148927    19529728   83  Linux
/dev/sda11      577150976   608399359    15624192   83  Linux
/dev/sda12      608401408   625141759     8370176   82  Linux swap / Solaris
/dev/sda13      420904960   459956223    19525632   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2 MB, 2097152 bytes
255 heads, 63 sectors/track, 0 cylinders, total 4096 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xffffffff

Disk /dev/sdb doesn't contain a valid partition table

Thank you for any help

---

### Post by oldfred on 2013-05-21
Moved to your own thread as other thread was dual boot with Windows.

Are you running RAID or had drive in RAID before? The sil error looks like a RAID type error. Drives need RAID meta data removed it not in RAID now.

Do not run this if you do have RAID.
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

Most desktops do not need separate /boot, but if you have a separate partition for /boot then you can not use it for any other install.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

    
If you overwrote a /boot partition you may be able to edit fstab and chroot into your install to reinstall grub & kernels.

---

### Post by fonsi2099 on 2013-05-27
till today no one of those options help to find s solution. the result are the same I can only boot my sda13 partition with the 12.04, but the sda2 partition with 13.04 is not more posssible to boot. 

 I think the next and most clean option will be to make a new reistallation of 13.04 and 12.04.02, Before backup your data!!!!!


many thanks to all  for your effort.

:popcorn:

---

### Post by fantab on 2013-05-27
Deleted. Got confused with antoher thread/post.

---

