---
title: "Windows 7 - PGP Whole Encryption Grub problems..."
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by abeowitz on 2011-02-11
So, my work laptop has Windows 7 with PGP Whole Disk Encryption on it.  

```
root@Lenovo-Abe:~# fdisk -luc

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x31addc30

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
/dev/sda2          206848   312578047   156185600    7  HPFS/NTFS
/dev/sda3       312578048   314675199     1048576   83  Linux
/dev/sda4       314675200   488397167    86860984   83  Linux

```
I've successfully installed Ubuntu and can boot to it from the grub menu.

The problems I'm having include these symptoms:

**sda1** - 
1)  os-prober does not recognize sda1
2)  blkid returns nothing for sda1 & sda2
2)  Cannot mount sda1 as ntfs, vfat or msdos
[B]
Grub2[/B]
Added standard windows 7 config to /etc/grub.d/40-custom:

menuentry "Windows 7" {
    insmod ntfs
    set root='(hd0,1)'
    chainloader +1
}

Experimented with adding part_msdos, too.  

And in /etc/default/grub:
GRUB_PRELOAD_MODULES="part_msdos"

***Grub2 always returns "Invalid Signature"***

And I've tried dozens of other hints found here and via Google.  No luck.

So, I'm wondering, is this partition really an ntfs or fat partition?  Or is the mbr a custom job bulk loading /dev/sda1?

***How should I modify grub to boot this wacky unknown partition type?***

(Working on a successfully imaged disk copy, btw.)

---

