---
title: "update-grub not picking up encrypted O/S"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by lloydh on 2013-02-07
New PC with 2 500MB hard disks.         Windows XP, Windows 7 and Ubuntu Gnome Remix 12.10 on the first disk and all working ok.

I install Centos on the second disk without a boot loader and then run update-grub in Ubuntu and Centos is added to the boot menu and it all works.

I delete the Centos install, run update-grub to clear Centos from the boot menu and then install Centos again with full disk encryption.         When I run update-grub in Ubuntu again it does not add Centos to the boot menu.           The Centos installation in both cases creates a 500MB boot partition  and the rest is a LVM partition.    With encryption the boot partition is not encrypted, only the LVM partition.

The output from fdisk -l

> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f3aac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   122884095    61441024    7  HPFS/NTFS/exFAT
/dev/sda2       122884096   245766143    61441024    7  HPFS/NTFS/exFAT
/dev/sda3       245766144   655368191   204801024    7  HPFS/NTFS/exFAT
/dev/sda4       655370238   976771071   160700417    5  Extended
/dev/sda5       655370240   943867903   144248832   83  Linux
/dev/sda6       943869952   976771071    16450560   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cfd01

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     1026047      512000   83  Linux
/dev/sdb2         1026048   976773119   487873536   83  Linux

Disk /dev/mapper/cryptswap1: 16.8 GB, 16845373440 bytes
255 heads, 63 sectors/track, 2048 cylinders, total 32901120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x77bb50ce

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
I'm not new to linux but very new to encryption and LVM, can anybody tell me what I need to do to get the boot loader in Ubuntu to recognise the Centos encrypted installation.

---

### Post by ahallubuntu on 2013-02-07
~

---

### Post by lloydh on 2013-02-08
> **ahallubuntu said:**
> Are you mounting the encrypted logical volume where CentOS lives before running update-grub ?
No, I assumed (how silly of me) that all grub needed to see was the boot partition.

I've done some reading since I first saw your post and I gather you are referring to the following commands.

pvscan
vgscan
vgchange -a y
lvscan
then mount everything seen by lvscan

I tried both lvscan and vgscan but they cannot see the volumes.

> sudo pvscan -v
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
    Walking through all physical volumes
  No matching physical volumes found

sudo vgscan -v
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
  Reading all physical volumes.  This may take a while...
    Finding all volume groups
  No volume groups foundIs this because it is encrypted and would it be because of the last line of output from fdisk which is.

> Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

---

