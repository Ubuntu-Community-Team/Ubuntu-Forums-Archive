---
title: "Misplaced boot record"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by advoss on 2006-08-19
I got Kubuntu installed on its own drive.  However when I turn on the computer it goes straight to the NT bootloader, and I can only get to GRUB by unplugging the drive with the NT bootloader on it.  How can I install GRUB on the HD that boots first and still keep access to the windows installations?

HDD Setup:
Kubuntu drive and another drive plugged into MOBO controller
Windows Drive (boot record) and another drive plugged into Promise ATA133 TX2 controller

The ATA133 drives don't appear in BIOS so I don't think I can change the boot priority to the Kubuntu drive

---

### Post by zxee on 2006-08-19
Interesting I have that same IDE controller card and my drives do show up in bios, but I don't think changing the boot order in bios is the answer anyway because of the way grub works. 
There is a slightly complicated way to use the windows bootloader to recognize and boot linux. There's a thread here [http://www.ubuntuforums.org/showthread.php?p=1396158#post1396158](http://www.ubuntuforums.org/showthread.php?p=1396158#post1396158) 
but there are also other howtos  do a search on NTLDR bootloader with linux.
You might be able to use the ubuntu cd to install grub-however if your bios doesn't detect those drives (bios runs first) it may not work-which is why I brought up the NTLDR method.

---

