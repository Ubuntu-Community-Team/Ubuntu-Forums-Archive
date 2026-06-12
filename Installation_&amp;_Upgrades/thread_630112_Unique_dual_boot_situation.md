---
title: "Unique dual boot situation"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by techgeek on 2007-12-03
I have been using Ubuntu for a few releases now and stumbled on a problem.  I was using Feisty 32 bit, and decided with this upgrade I would try Gutsy in the 64bit variety.  I dual boot Win XP Home with Ubuntu with Windows on the first partition which is pretty much standard.  I use the default GRUB bootloader.  I have my HDD's SATA controller set to AHCI (aka NCQ).  Everything worked fine with Feisty with this setup.  I booted from the CD (which I find to be a hit and miss situation no matter which version) and installed Gutsy 64 bit over Feisty.  Everything went fine as I expected (partitions re-formatted, files copied, GRUB installed) and I rebooted.  GRUB came up fine which means that the bootloader had access to /boot/grub/menu.lst, but when I selected Ubuntu to boot, I got a partition doesn't exist error message.  When I tried to boot Windows, I received a read error message.  Now this isn't my first time around the block with bootloader problems.  I re-boot using my Windows CD using my F6 floppy drivers for AHCI and did a repair (fixmbr).  This got me back to booting into Windows fine, and of course orphaned my linux partitions.

Now the question, has anyone seen this before?  At first I thought it had something to do with AHCI, but if it were, the linux partitions would not have been available thus /boot/grub/menu.lst wouldn't be accessible to the bootloader and I wouldn't have gotten a menu at all.  Also if it was an AHCI problem, the installer wouldn't have been able to see the HDD or any of it's partitionsl.  The Windows error seems to indicate that GRUB was interfering with AHCI for Windows though, since this error message is the same as if you installed Windows using IDE and then switched it to AHCI in the BIOS afterwards.  So is this something to do with the 64 bit version, or AHCI?  As I said before, I was running 32 bit Feisty in this environment before.

Any assistance with identifying the root cause would be great.

---

### Post by Craigus on 2007-12-03
Can post the relevant section of menu.lst ?

---

### Post by logos34 on 2007-12-03
and the output of 

sudo fdisk -l

---

### Post by techgeek on 2007-12-03
I think I might have it sorted out.  I am installing right now.  It seems had I been looking closer during the install, when I was installing I had my external USB harddisk plugged in.  I was enumerating it as sda and my SATA drive was being enumerated as sdb.  During boot up though it would see my SATA drive as sda and therefore the error messages.  I am about to reboot and I think everything should be fine, I will post the results.

---

### Post by techgeek on 2007-12-03
Yeah that was the problem.  I installed without the USB drive plugged in and it enumerated my internal drive properly.  So it installed, but I have a few wrinkles to work out.  First off no sound.  I have a HD2900XT and it defaulted my playback device to the audio portion of my graphics card.  Same thing Windows did.  Fortunately for Windows, all I had to do was change my default device and it worked.  Unfortunately this didn't work for Ubuntu.  Also when I play back a MP3 (even though I can't hear anything), the rate of playback seems sped up.  Next I installed the restricted drivers for my video card, and now when it goes to the log in screen I am greeted by a black screen and the computer doesn't respond to CTRL-ALT-DEL.  So it looks like it's off to ATI to download the drivers directly.  Oh well don't you just love linux.

Is it just me or does this version just not seem to be as polished as previous versions.  Edgy and Feisty seemed much better IMO.

---

