---
title: "[SOLVED] (at least for me!) GRUB errors - 15, 18, 22 while install/upgrade to 8.10"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by oledocmeth on 2008-11-09
Once upon a time - a server refused to run 8.10 - the trial and tribulations to get it to work.

I had move 2 notebooks to 8.10 with ease.  It was dealing with an older machine that I had turned into a file/printer server, when the saga began.

I was getting GRUB errors left and right, mostly before you could even get to the point of editing the boot settings.
GRUB error 15: File not found
GRUB error 18: Selected cylinder exceeds maximum supported by BIOS
GRUB error 22: WTF!!

NOTE: at no time did booting the CDROM in rescue mode and messing with GRUB commands solve ANYTHING!!!!

Things that may have led to my problems --
Used a 300GB drive to boot
Was using one huge partition mounted as "/"
    (NOTE: partition setup on CDROM defaults to this)
Was using JFS file system instead of default ext3
Had fast wide SCSI drives that when booting from cd where id'd as /dev/sdb and /dev/sdc and my IDE drive was /dev/sda as I expected.  But when booting the 8.10 kernel (2.6.27-7), the SCSI drives became /dev/sda and /dev/sdb, while my boot drive became /dev/sdc - very annoying and confusing!!! 

My solution -

I pulled all other drives, leaving the 1 300GB. (not sure this did anything, but ruled out a lot of possible problems).

Created a separate 300MB ext3 partition for /boot at front of drive, then 4GB SWAP partition, then root ("/") JFS file system for the rest of the drive.

I also added "rootdelay=40" to the GRUB defoptions line in file "/boot/grub/menu.lst", as well as to the end of any lines that started with "kernel" at the bottom.

---

