---
title: "Install dual-boot with dmraid on gpt disks"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by jlc2010 on 2011-01-26
Hi,

I'm trying to install Ubuntu 10.10 on an existing Windows7 system.  The win7 system is on a separate Intel SATA RAID1 array.  The drives are formatted MBR & win7 is running w/o a problem.  I want to set up a separate dmraid RAID1 array with another pair of disks, formatted GPT.  I created the array in BIOS,  then from Live CD used gdisk to partition the array & install the OS.  I attempted to use EasyBCD to boot the Ubuntu install from Windows & when that failed, I booted with Super Grub2 Disk to see if I could figure out the problem.  The Ubuntu array partitions look like this:

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          411647   200.0 MiB   EF00  EFI System
   2          411648          413695   1024.0 KiB  EF02  BIOS boot partition
   3          677888         1087487   200.0 MiB   0700  Linux/Windows data
   4         1351680        51683327   24.0 GiB    8200  Linux swap
   5        51947520      1953519846   906.7 GiB   0700  Linux/Windows data

Partition 3 holds /boot & 5 has /.  Looking at partition 5 from the GRUB2's bash prompt, I don't see any files in /dev/mapper for the GPT partitions, only "control".  From the Live CD, I ran kpartx & can see it could create the right entries for the array, but it looks like the installer didn't do it.  Is there a way I can manually fix this up, or did I miss a step?

Thanks.

    -John

---

