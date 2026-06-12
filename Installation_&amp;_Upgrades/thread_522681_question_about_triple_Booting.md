---
title: "question about triple Booting"
date: 2007-08-10
forum: Installation &amp; Upgrades
---

### Post by Jason_howard on 2007-08-10
I have 2 hard drives one has Vista and Ubuntu 7.04. I want to put Freespire 2.0 on the other Harddrive does anyone have any recomendations how how to install this without messing Vista up.

Another question would grub pick up all 3

---

### Post by Pumalite on 2007-08-10
Just install Freespire. Then re-install Ubuntu's Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Or use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Ubuntu's Grub will pick them all up.

---

### Post by MQMike on 2007-08-11
Install Freespire to the second hard drive, but do NOT let the Freespire (FOS) installer put GRUB in the Master Boot Record (MBR) of anything!  Just tell it to put GRUB in the same partition as you are putting Freespire (on your second hard drive).

I assume Ubuntu’s GRUB was controlling the dual-boot before all this?
If so, edit the boot menu in Ubuntu (/boot/grub/menu.lst) to include and entry for Freespire, and get that entry by copy/pasting the actual FOS entry from Freespire’s menu.lst.

If, on the other hand, Vista was controlling the boot menu for booting, then you may be able to edit the Vista bootloader using EasyBCD to include a new entry for FOS.

- - - - -
NOTE about FOS:


It has two menu lists!
boot/grub/menu-sdb=hd1.lst
boot/grub/menu-normal.lst
 
The “real” or usable menu.lst kept at FOS for booting FOS and the other OSs is menu-sdb=hd1.lst.  Use this one.  Get into it and copy the entry for Freespire, paste it into your Ubuntu menu.lst on the first hard drive.
It will look something like:

# sdb5, boot entry for FOS
title Freespire Ver. 1.0.13
root (hd1,0)     # Comment: Your (hdx, y) may be different here
kernel /boot/vmlinuz-2.6.14-gratis  root=/dev/root rootdev=0x0815 ramdisk=35392 video=vesafb:nomtrr jiffymount=noatime resume2= vga=0x311 splash=silent
initrd /boot/initrd-2.6.14-gratis.gz

- - - - -

***   The definitive dual-booting guide: Linux, Vista and XP step-by-step
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)


Reinstall GRUB:

Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)
(the classic reference for dual booting)

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(Re-install GRUB and editing the menu.lst and other stuff)

I’m guessing that you can probably get into EasyBCD editor and force it to include an entry for Ubuntu.

---

