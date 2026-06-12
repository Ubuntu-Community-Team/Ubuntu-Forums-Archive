---
title: "Unable to find a medium containing a live file system"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by Matheus_Cansian on 2013-10-20
Guys, I'm having trouble installing Ubuntu 12.04 (64bit) on my Acer laptop. 

Every time I boot from an USB drive, it goes to the BusyBox with the following error:
[I]Unable to find a medium containing a live file system

[/I]I've already tried some of the suggestions from other threads, but none of them works. What I have tried so far:
1. acpi=off
2. Disconnect all USB devices, but the drive
3. Change SATA to AHCI (it's already my default)
4. Check for OS detection on the BIOS (my BIOS doesn't have this)
5. MD5SUM the ISO file (It was ok)
6. Try creating the bootable USB with different softwares (I tried with the Startup Disk Creator and Unetbootin on Ubuntu; and Linux Live USB Creator on Windows)
7. Change USB ports - I've tried on all USB ports on my laptop

Additional information:
* I have already installed Ubuntu in this computer (12.04 and 13.04). I currently have 13.10 (upgraded from 13.04), but I'm trying to downgrade to 12.04.
* I recently made a BIOS update to solve an issue involving Acer laptops and battery detection. This BIOS update was made AFTER I have installed Ubuntu, so I guess that this is the problem. The weird thing is that even when I disable ACPI, I get the same error.
* If boot from my installed version it goes smoothly. In fact, I'm using Ubuntu right now.

Laptop: Acer Aspire 5745-3428
Current OS: Ubuntu 13.10 and Windows 7

Could you guys help me? I'm kinda lost
Thanks!!

---

### Post by Bucky Ball on 2013-10-20
> Unable to find a medium containing a live file system

Would have thought this suggested there is something wrong with the USB device. Booting from USB, the system can't find anything (a live filesystem) to boot from.

---

### Post by Bucky Ball on 2013-10-20
> Unable to find a medium containing a live file system

Would have thought this suggested there is something wrong with the USB device. Booting from USB, the system can't find anything in the USB slot to boot from.

---

