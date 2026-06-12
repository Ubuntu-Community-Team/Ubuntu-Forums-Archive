---
title: "Windows 7 - Boot Select failed"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by draucia on 2012-10-23
EDIT: Fixed it. What I did was I manually took the boot flag (using gparted) off of /dev/sda1 (recovery enviroment) and put it on /dev/sda2. Then I booted the windows repair CD and it prompted me with a message with something like "Windows will automatically add Windows 7 to the list" (or something like that, can't remember), I clicked "Repair and reboot", and it worked.

The first time I installed ubuntu it went well, no problems. But I did a bit of distro hopping (to see if it could solve on of my problems), and I decided to just stick with ubuntu 12.10. When the installer finishes installing, I have to manually install grub with the --root-directory=/mymountedubuntu/ /dev/sda, and it installs grub with both "Ubuntu" and "Windows 7" options.

The problem is, when I select Windows 7 it says "Boot Select failed because a requested device is inaccessible."

If I put in my Windows repair CD and do the:

bootrec.exe /firMbr
/FixBoot
/RebuildBcd

It fixes it, but I don't have grub anymore and I can only boot to windows. How can I have both working?


```
sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc34542a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   745768457   372780805    7  HPFS/NTFS/exFAT
/dev/sda3       745768960   960612351   107421696   83  Linux
/dev/sda4       960612352   976771071     8079360   82  Linux swap / Solaris

```

---

