---
title: "GRUB, Ubuntu and Windows boot problem"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by raj727 on 2007-08-05
I'm having a problem booting into Ubuntu and Windows XP.

I initially installed Ubuntu 7.04 on my second hard drive (a SATA drive).  But when I went to boot, I kept going into Windows.  A friend checked my BIOS and determined it only recognized the first hard drive (possibly an IDE drive) and not the second hard drive.  I then reformatted the second hard drive for use in storing files and installed Ubuntu on the third partition of the first hard drive (the first partition had the Windows XP operating system while the second partition had Windows programs and files).  When I booted I kept going into Windows without any GRUB menu.  I then disconnected the second hard drive and reset GRUB (using sudo grub, find.., root..., setup..., quit) but started getting a GRUB error 21 message.  I then reconnected the second hard drive and reset GRUB using the same commands as before.  However, when I entered "find /boot/grub/stage1" I got a GRUB error 15 message.  At this stage I was not able to boot into either Ubuntu or Windows but I did start getting a GRUB menu.

At a forum member's suggestion, I downloaded the SUPER GRUB DISK (SGD) and followed the instructions to fix the Ubuntu and Windows boot problem.  After rebooting, I tried to go into Ubuntu choosing the kernel 2.6.20.16 generic option.  However, I got an "Error 22: No such partition" message.  I then tried going into Windows using the MS Windows XP option.  I got a message saying this not a bootable disk.  After that, I got a message about a Pre-boot eXecution Environment (PXE) v2.1 saying "no boot filename received".  A further message stated, "disk boot failure, insert system disk and press enter".  I hit enter (without inserting any system disk) and went back to the GRUB menu.  However, just before the GRUB menu I saw a quick statement about GRUB 5.1 on screen.  I then again chose the kernel 2.6.20.16 option and suddenly I found myself booting into Ubuntu without any explanation.

When I shutdown Ubuntu and try to reboot, I get the same problems as before.  However, if I follow what I did before I'm able to boot into Ubuntu.  I've done this several times and found this is the only way I can boot into Ubuntu.  I'm still not able to get into Windows.  I need Windows because my son would rather use Windows.

I'm not sure what options I have.

---

### Post by RevThain on 2007-08-05
I have had the same problem in the past with a version of Knoppix. The same thing applies here... It DOES matter what order you install the two operating systems. Windows, unfortunately, chooses a different patition and makes it active if you don't install the OS's in the correct order. Grub will not find the partition... Most of the time the "boot" partition is hda1. After a few installs of knoppix, windows changed to hda3. Go figure.

 Unfortunately, the only fix I know of is to install windows first, then any other OS. Windows does not support multi-booting any other OS but Windows. But, someone may know the answer to this, so don't give up yet.

---

### Post by fumduck on 2007-08-05
try this 
[http://apcmag.com/dualboot]("http://apcmag.com/dualboot")

it may or might not help but it might point you in the right direction
Peace
M

---

