---
title: "want to install Ubuntu but"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by ericthered8 on 2009-12-15
Hello all,
 
I would like to install Ubuntu koala on an empty partition, with the other partition housing Windows 7, but I would like to keep windows boot manager intact and be able to choose which OS to boot at startup.
 
I have tried to install Ubuntu in the past, and it made my other partition with Windows 7 unbootable and I was forced to format.
 
The problem is I have no cd/dvd drive to repair Windows 7 if Ubuntu does cause it to be unbootable and so I would like to avoid this.
 
Any suggestions? Thanks

---

### Post by recluce on 2009-12-15
> **ericthered8 said:**
> Hello all,
 
I would like to install Ubuntu koala on an empty partition, with the other partition housing Windows 7, but I would like to keep windows boot manager intact and be able to choose which OS to boot at startup.
 
I have tried to install Ubuntu in the past, and it made my other partition with Windows 7 unbootable and I was forced to format.
 
The problem is I have no cd/dvd drive to repair Windows 7 if Ubuntu does cause it to be unbootable and so I would like to avoid this.
 
Any suggestions? Thanks

It may not sound helpful, but you really should get a CD drive - just in case, so that you can start rescue media.

Other than that, you will get GRUB as your bootmanager, which will allow both Ubuntu and Windows to boot. Personally, I would be tempted to install Ubuntu 9.04 in your situation, since GRUB 2 (with 9.10) seems to cause much more problems than the old GRUB. Or, to be brutally honest: I would avoid any installation until getting that CD drive...

---

### Post by ericthered8 on 2009-12-16
Thanks for your reply
I guess I have no issue using grub as a boot manager if indeed Windows 7 will boot
 
I just dont want to have to repair Win 7 after installing Ubuntu because I will be stuck
 
is this possible? also what happens if grub does not give the option to boot windows and boots into ubuntu automatically?

---

### Post by cholericfun on 2009-12-16
dunno bout grub2 but legacy grub should have no problem letting you boot into windows.

find out how you can get to a windows recovery session and what to do there to restore the MBR. you prob. have a small partition with some sort of windowsrecovery on it?

alternativly check your friends to see if anyone has a usb-cddrive
or normal cd-drive

---

### Post by llawwehttam on 2009-12-16
try gag as your bootloader. Ive never had problems with it .
[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

