---
title: "Windows won't boot, stuck.. please help!"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by demonr675 on 2008-09-19
Somehow I managed to screw things up royally and need help. I was going to install Ubuntu on another drive I have. I loaded the bootable cd and it asked me if I wanted to created a bootloader in my Windows drive so I can run Linux the next time I booted. I did, it booted and installed Linux on the other drive. On reboot now I can't get into anything. I get an error as follows..

GRUB loading, please wait..
Error 21

I don't want to boot into Linux, I did not expect it to screw up my Windows install now I am stuck. I can't get into Linux, I can't get my Windows machine to boot and I need to fix it. I have the drive piggybacked into the system I am on now and I can explore it in Windows, trying to figure out what I need to edit/delete/fix so I can get into Windows again. Please help..

---

### Post by cypherzero on 2008-09-19
GRUB cannot find its setup files.
Make sure the disk you installed Linux on is connected to avoid Error 21.

I had this same problem, I created a small partition on my main disk and installed GRUBs files to here to avoid having to keep my external disk connected.
*Internal Disk:*
[COLOR="DarkSlateBlue"]  GRUB Bootloader
  1. 40Gb NTFS (Windows XP)
  2. 8Mb XFS3 (GRUB config files)[/COLOR]
*External Disk:*
[COLOR="darkslateblue"]  No boot sector.
  1. 200Gb FAT32 (Misc files)
  2. 4Gb Swap (Linux Swap)
  3. 50Gb XFS3 (Linux - also where GRUB config files were originally installed)[/COLOR]

If somehow GRUB has lost its setup files (lets say they got deleted or moved) all you need to do is reinstall GRUB.

This is presuming you have the same issue I did!

---

### Post by demonr675 on 2008-09-19
Well, what happened in my case is that I wanted to install it on another drive separate from my Win drive. Somehow it altered something on my Win drive and cocked it up so now it wants to dual boot. Not something I wanted to happen. The question now is what did it alter on the Win drive that I have to fix. :(

---

