---
title: "Crashed during installation upgrade to 22.04...can no longer boot into OS"
date: 2022-08-31
forum: Installation &amp; Upgrades
---

### Post by rorybellows2 on 2022-08-31
I was trying to upgrade my Ubuntu 20.04 to 22.04 and halfway through the installation process I got an error message stating, "Oh no!  Something has gone wrong and the system can't recover.  Please log out and try again."  When I click on the log out button it takes me back to the same error message screen.  Rebooting also took me back to the same screen.  

I've been trying to repair GRUB bootloader using a bootable USB stick and then running boot-repair with only more errors:

1) I was instructed to run the following command:
   $sudo chroot [directory] dpkg --configure -a

   error message:  
       Errors were encountered while processing:
           netplan.io
           systemd

2) I attempted to do run the "Recommended repair" again and got this error message:  grub-efi purge cancelled.


My pastebin is here: [https://paste.ubuntu.com/p/PSbXnb9swn/](https://paste.ubuntu.com/p/PSbXnb9swn/)


Please help!  I'm not even sure if I'm going about this the right way to fix everything.  Thank you in advance.

-Rory

---

### Post by oldfred on 2022-09-01
Did you uninstall the nVidia proprietary driver before upgrading.
Often upgrades do not work with any proprietary drivers or ppa. They all need to be uninstalled & then reinstalled after upgrade to be correct.

You also have a newer UEFI system, but still have grub installed in MBR. Just never try to boot in BIOS mode as your install is UEFI.
You also have the old MBR(msdos) partitioning. UEFI suggests gpt. Windows requires gpt for UEFI installs. But Ubuntu will let you install in UEFI mode to MBR drive and probably should not.

But to convert to gpt normally erases drive, so good backups required.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)

converting to gpt should only be considered if you can resolve your errors or if you decide to do a new clean install.
This really works best for data only drives. UUIDs all change so fstab entries need updates & grub total reinstall required, if done on a system drive.
Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

