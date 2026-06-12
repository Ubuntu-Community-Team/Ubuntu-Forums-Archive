---
title: "Dual Booting with Two Seperate Drives"
date: 2005-09-18
forum: Installation &amp; Upgrades
---

### Post by TheTK421 on 2005-09-18
Sorry if this has been asked or awnsered before, but how do you install XP and Ubuntu on two seperate drives? I finally got XP reinstalled, but I need Linux for programming (I love KDevelop) and I am more comfortable with it, but I have never dual booted across multiple drives with XP and GRUB. I know that XP needs to be installed first and located on Master/Primary, but is there anything else special that needs to be done? 

Here is the setup I am hoping to use:
IDE Drive 1:
Master/Primary
GRUB in the MBR
230GB NTFS for Windows

IDE Drive 2:
Slave
76GB partition for Ubuntu
1GB Swap

Will this work without a lot of trouble/problems, and will Ubuntu automatically see both and configure GRUB accordingly?

Thanks in advance,
TheTK421

---

### Post by foxzilla on 2005-09-18
Just something I did for my install of Ebuntu Linux on two hard drives. Xp is installed on the master drive and Ebuntu to the slave. When Ebuntu did the install I chose to format the slave drive to EXT3 file system and did a Grub boot from floppy. It works great. The bios is set up to boot from floppy first and Master drive second. If you want to have an extra copy of your floppy for the boot I used Winimage "using WINXP :-(" to burn extra copies . I would think a backup of the Grub boot floppy might save you from future problems. Floppy's tend to somewhat unreliable. Just MHO.

---

### Post by alainhenry on 2005-09-19
I had some problems with a similar situation because I initially formatted the drives with Linux and not Windows.  I suggest doing the initial formatting with the windows install disk, and then reformatting when needed with Ubuntu.  A long discussion on this can be found in thread: 

[http://www.ubuntuforums.org/showthread.php?t=40197](http://www.ubuntuforums.org/showthread.php?t=40197)

Alain

---

