---
title: "Installation Help"
date: 2005-04-22
forum: Installation &amp; Upgrades
---

### Post by lark012 on 2005-04-22
Hi,

I'm trying to install Ubuntu Hoary and dual boot it with my Windows XP partition.  I've been searching the forums and the web, but I cannot find a solution to this problem.  Here it is:

I have 3 hard drives in my computer:
1 SCSI (Windows XP here)
1 60 gig IDE (backup/storage for windows XP)
1 160gig (Ubuntu here)

I've ran the setup several times now, but each time, the Grub loader doesn't work and it boots directly to Windows XP.  I've tried to manually place grub on one of the hard drive's boot sector, as well as the MBR and a floppy, but no success.   Can anyone point me to a previous thread that could solve my problem, or if you have any tips that I can take?  Thanks much!

---

### Post by heimo on 2005-04-22
Which hard disk did you put the grub on? Was that hard disk selected as a first boot disk in BIOS boot order? And when using floppy, did you select it as a boot device?

Do you see grub at all, or does it go straight to Windows? That'd mean that grub is not loaded at all. I believe it's possible to add Linux to Windows boot loader (I've done it with NT) - so it'll jump to your 160GB disk, load Grub and boot Linux. Or you can make your system boot from that 160GB disk, add Windows to menu.lst (Grun configuration file) - or you can just switch between operating systems with BIOS settings.

---

