---
title: "Grub fails after successful install"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by pmatos on 2008-03-23
Hello all,

I am trying to install ubuntu replacing fedora, which had also windows. 
The system is composed by:
- sda1 : one ntfs backup partition
- sda2 : main ntfs windows partition
- sda3 : swap partition
- sda4 : extended partition
- sda5 : / partition inside sda4

In the end of the install grub says it fails to install grub and now my system is unusable.
I tried to install grub through the livecd.
I mounted sda5 onto mnt, chrooted into mnt and then tried a grub-install, however, there's no /dev/sda5 in (mnt)/. I might guess this has something to do with udev or similar...

Any ideas on how to get this working?

Cheers,

Paulo Matos

---

### Post by Oldsoldier2003 on 2008-03-23
> **pmatos said:**
> Hello all,

I am trying to install ubuntu replacing fedora, which had also windows. 
The system is composed by:
- sda1 : one ntfs backup partition
- sda2 : main ntfs windows partition
- sda3 : swap partition
- sda4 : extended partition
- sda5 : / partition inside sda4

In the end of the install grub says it fails to install grub and now my system is unusable.
I tried to install grub through the livecd.
I mounted sda5 onto mnt, chrooted into mnt and then tried a grub-install, however, there's no /dev/sda5 in (mnt)/. I might guess this has something to do with udev or similar...

Any ideas on how to get this working?

Cheers,

Paulo Matos

try using the [SuperGrub Live CD]("http://supergrub.forjamari.linex.org/") it has a few more options for reinstalling grub, it should be able to fix the problem for you.

---

### Post by housam on 2008-03-23
boot from the live CD and type in the terminal ```
sudo fdisk -l 
```
where -l is a small L and post the results

---

### Post by pmatos on 2008-03-23
> **housam said:**
> boot from the live CD and type in the terminal ```
sudo fdisk -l 
```
where -l is a small L and post the results
[INDENT]
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x489b470e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1627    13063168   27  Unknown
/dev/sda2   *        1627       30108   228770968    7  HPFS/NTFS
/dev/sda3           30109       30133      200812+  82  Linux swap / Solaris
/dev/sda4           30134       36481    50990310    5  Extended
/dev/sda5           30134       36481    50990278+  8e  Linux LVM[/INDENT]

---

### Post by housam on 2008-03-23
> **pmatos said:**
> [INDENT]
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x489b470e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1627    13063168   27  Unknown
/dev/sda2   *        1627       30108   228770968    7  HPFS/NTFS
/dev/sda3           30109       30133      200812+  82  Linux swap / Solaris
/dev/sda4           30134       36481    50990310    5  Extended
/dev/sda5           30134       36481    50990278+  8e  Linux LVM[/INDENT]

you have a swap partition . but you don't have an ext3 partition as a root ( / ) for ubuntu. use Gparted tool ( in the live CD ) to reformat sda5 to ext3 format and reinstall ubuntu.( post a screen shot of your partition table when using Gparted ).

---

