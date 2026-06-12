---
title: "Ubuntu just killed my lappy, (boot sector issues)"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by Stochastic on 2006-09-08
Hey, I was trying to re-install ubuntu on my dual boot (to get my broadcom 4318 working) and in the process of the gui installer it somehow wiped the boot sector of my partitions from what I can tell.  I was resizing partitions but not writing to them, and I saw the installer attempt to call my ntfs filesystem an ext3 so I went back a step and lo and behold it could no longer recognize my partition types (and the sizes wern't what I was resizing to).  I exited and restarted without the install cd and grub gave me an error 17.  Is there any way to get my data back?  My roommate will kill me if I lose some of that data and I'll hurt myself if I loose all the proprietary programs that I spent hard earned money on (why was I so stupid).  Please Help!!!

---

### Post by tribaal on 2006-09-08
Try to boot off the liveCD, and mount your harddisk(s). From there you should be able to copy all important info, if you didn't screw up the partitions themselves.

Don't want to put salt on the wound, but... you should really *backup* your data before messing with partitions.

Good luck.

- trib'

---

### Post by Stochastic on 2006-09-08
I can't mount the windows partition in the live cd, I've tried editing the /etc/fstab file for it to mount as a ntfs(which is what it was and should be) and ext3(which is what 'fdisk -l' called it) and both times I get the message:

mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail or so

then when I try dmesg | tail i get this:

[4295162.471000] SGI XFS Quota Management subsystem
[4299183.318000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4299183.318000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4299183.319000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.
[4299202.952000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4299202.952000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[4299202.953000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.
[4299265.920000] VFS: Can't find ext3 filesystem on dev hda1.
[4299407.595000] VFS: Can't find ext3 filesystem on dev hda1.
[4299407.596000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

any help on mounting this, I have room on another partition to rescue data.  Oh, and in my defense for backing up the data, I really didn't think I was going to resize this partition, then I decided on a whim to do so to give windows a little more headroom (man why did I do that).  Thanks.

---

### Post by Stochastic on 2006-09-08
After reading those errors, I tried adding "errors=recover" to the hda1 string in /etc/fstab and now I get these errors through dmesg | tail:

[4299838.108000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[4299838.527000] NTFS-fs warning (device hda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[4299838.527000] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Could not find a valid backup boot sector.
[4299838.527000] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.

---

### Post by Stochastic on 2006-09-08
Does this mean the partition is effered?  is there any way to recover the data?

---

### Post by Stochastic on 2006-09-09
Anyone???  does anyone know if I can recover the data on this partition?

---

### Post by Stochastic on 2006-09-09
one last bump.  please help, it's kinda urgent.

---

### Post by ringmaster on 2006-09-13
> **Stochastic said:**
> one last bump.  please help, it's kinda urgent.

There is a free GPL utility to recover data from broken hard disks, it analyses the HD recovering the files that you specify (e.g. *.jpg), repairs boot sectors and a lot more and runs with a boot CD:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Please read the documentation carefully to recover your data fast and successfully.

---

### Post by marcelm on 2006-09-14
have a win xp installation? try recovery console and type fixboot.

---

