---
title: "Dual boot Vista on Raid-0 and Ubuntu on third disk"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by gvanecek on 2008-07-01
I have a Dell XPS 720 running Vista on two 160G drives in Raid-0. I added a 500G drive on which I installed AMD-64 Ubuntu 8.04 from the LiveCD.

Because of Vista on the RAID-0 drives, I didn't want to overwrite MBR with grub as I read that RAID-0 drives require non-standard installation; so during installation I left out the GRUB installation. Trying to install grub manually now just cannot seem to configure grub on the /dev/sdc disk and update the MBR to dual boot.

When I reboot into the liveCD I can mount my Linux fs from /dev/sdc1. FDisk gives:
[INDENT][FONT="Arial"]Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313       38905   301956092    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005d669

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       59326   476536063+  83  Linux
/dev/sdc2           59327       60801    11847937+   5  Extended
/dev/sdc5           59327       60801    11847906   82  Linux swap / Solaris
[/FONT][/INDENT]

If I mount /dev/sdc1 as /media and *sudo grub*, when I do *find /media/boot/grub/stage1* I get **Error 15: File not found**.

When I try to *sudo grub-install /dev/sdc* I get **Could not find device for /boot: ...**.

So, now I'm stuck. What do I need to do to install Grub on my sdc disk so that it sees my Raid-0 Vista on /dev/sda and /dev/sdb and Ubuntu on /dev/sdc?  All the posts that talk about this simply have you start with the grub find so they're not much help.

---

### Post by gvanecek on 2008-07-01
One option I am considering is to reinstall Linux on the sdc drive and this time have it do the default install of GRUB. Since the RAID-0 is not recognized but instead it sees both sda and sdb as separate disks, what would the setting be?

---

### Post by gvanecek on 2008-07-01
Ok, I reinstalled Ubuntu on /dev/sdc and this time I enabled the GRUB to install on the /dev/sdc drive. I then configured grub:
[INDENT]$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd2,0)
grub> root (hd2,0)
root (hd2,0)
grub> setup (hd2)
setup (hd2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd2) (hd2)1+16 p (hd2,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
[/INDENT]
When I rebooted and pressed F12, Windows booter showed the SATA drive as an optional boot drive in addition to the CD-ROM and the RAID-0 array. Selecting the Linux SATA drive successfully found GRUB and showed 3 bootable images. 

But now when I select any of the images in GRUB to boot, I get:
**Error 17: Cannot mount selected partition.**
Now what?

---

### Post by gvanecek on 2008-07-02
I changed hd2 to hd0, (*grub> setup (hd0)*)then edited the bios to boot the linux disk first and now when I select the third disk it boots fine.

The final result is that the original RAID-0 Vista disk and its MBR is not changed, so that the use of the Linux disk is transparent to the original Vista boot.  Best part is that the third GRUB bootable SATA disk with my Linux now appears when I press F2 to manually load Vista. Thus if I wipe out Linux there is nothing to undo on my RAID-0 array.

---

