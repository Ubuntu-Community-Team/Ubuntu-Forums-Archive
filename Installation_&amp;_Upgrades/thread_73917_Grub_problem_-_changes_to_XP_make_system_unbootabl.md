---
title: "Grub problem - changes to XP make system unbootable"
date: 2005-10-10
forum: Installation &amp; Upgrades
---

### Post by mislem on 2005-10-10
Hi everyone
   I've got a WinXP laptop (DELL D600) and I partitioned the HD (24 GB win, 13 GB ubuntu, and whatever Ubuntu set up for the swap) and installed Ubuntu with no problems.  Booted fine after install, ran all the updates, everything was still fine.  Worked fine in both Windows and Linux.  Two days later, I installed a program on Windows XP and rebooted.  The system wouldn't boot. 
 
   The Dell BIOS screen would come up, then it would go black (rebooting), then the BIOS screen again, then reboot, on and on.  So, I fdisk 'ed the MBR, and Windows came up just fine.  I then removed and reinstalled Ubuntu, and everything was working fine again after several reboots and logins to both systems.  

   Until I again installed another program on Windows XP.  Rebooted, and all of a sudden the GRUB bootloader doesn't seem to be working any more, same problem as before.  There are no errors that I can see, unless they flash up on the screen so fast that I can't see them before the system reboots.
   Anybody have any idea what I'm doing wrong, or what I can do to correct this?  I'd really like to use Ubuntu, but if I can't install anything in Windows any more, it's not really an option.

Thanks for the help, all.

---

### Post by aysiu on 2005-10-10
What are these programs you keep installing? Normally programs (like Firefox or Blender or iTunes) don't necessarily interfere with the boot record.

---

### Post by mislem on 2005-10-10
Adobe Creative Suite 2 and Office 2003

---

### Post by mislem on 2005-10-11
Well, I reinstalled and chose "Go Back" when Ubuntu got to the part where you are asked to install GRUB.  I noticed the option to install LILO, which I did.  After a little tweaking of the lilo.conf file, I was able to get everything up and running.  I installed several big apps on Windows and rebooted successfully.  So I think my problems are over.  Hooray for LILO...

---

