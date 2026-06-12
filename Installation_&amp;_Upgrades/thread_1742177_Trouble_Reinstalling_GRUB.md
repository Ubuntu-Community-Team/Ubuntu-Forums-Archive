---
title: "Trouble Reinstalling GRUB"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Jaken Veina on 2011-04-28
Running a dual-boot laptop with Windows 7 and Ubuntu 10.10. I recently reinstalled Windows 7 to get a fresh start, keeping the Ubuntu installation intact. Upon re-installing GRUB, I get a black-screen on boot. 

I've been using the following instructions for re-installing GRUB: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) , [http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

Running from a 10.04 Live USB, the specific commands are....

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbe13d29e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        6540    52428800    7  HPFS/NTFS
/dev/sda3            6540       14497    63909888    7  HPFS/NTFS
/dev/sda4           14498       19457    39841169+   5  Extended
/dev/sda5           14498       15492     7992306   82  Linux swap / Solaris
/dev/sda6           15493       19457    31848831   83  Linux

Disk /dev/sdb: 4012 MB, 4012900352 bytes
120 heads, 55 sectors/track, 1187 cylinders
Units = cylinders of 6600 * 512 = 3379200 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1188     3918832    b  W95 FAT32
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$

```The Live USB confirms that all the files in the original Ubuntu partition are still intact.

Upon boot, all I get is a black screen, which flashes white from time to time, like it's trying to load something. If I hold SHIFT while booting, I do see "Loading GRUB..." for a brief moment, before getting the black screen.

Any ideas? Thanks in advance for any advice.

---

### Post by cbowman57 on 2011-04-28
I used to do the "restore from LiveCD" thing but now I just keep a copy of Rescatux burned to a CD.  Simplifies the whole process.

[http://www.supergrubdisk.org/?page_id=61]("http://www.supergrubdisk.org/?page_id=61")

---

