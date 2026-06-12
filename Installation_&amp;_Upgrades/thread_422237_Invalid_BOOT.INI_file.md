---
title: "Invalid BOOT.INI file"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by Captain Obvious on 2007-04-25
I'm a total newbie when it comes to Linux.  I downloaded the Ubuntu 7.04 Desktop ISO file.  I burned it to a CD and changed the BIOS to boot the CD drive first and my USB second (i am trying to install to a USB External HDD).  Upon booting, i recieved the message "Invalid BOOT.INI file" and then it booted windows from the C: drive.  Next, i tried extracting the files from the ISO and burned them to a disc.  I got the same results, however, now the Ubuntu 7.04 DiscTree opens in windows.  It says that if I reboot, i can run the live version, but this doesn't work.  Where am I going wrong?

I have:
Toshiba Satellite A105-S4074 Notebook
Intel Centrino Duo Processor
Toshiba MK1234GSX Internal HDD (120 GB)
Travelstar IC25N040 ATMR04-0 USB External HDD (from old Gateway notebook)
Matshita DVD-RAM UJ-841S CD/DVD drive

---

### Post by kagashe on 2007-04-25
> **Captain Obvious said:**
> I'm a total newbie when it comes to Linux.  I downloaded the Ubuntu 7.04 Desktop ISO file.  I burned it to a CD and changed the BIOS to boot the CD drive first and my USB second (i am trying to install to a USB External HDD).  Upon booting, i recieved the message "Invalid BOOT.INI file" and then it booted windows from the C: drive.  Next, i tried extracting the files from the ISO and burned them to a disc.  I got the same results, however, now the Ubuntu 7.04 DiscTree opens in windows.  It says that if I reboot, i can run the live version, but this doesn't work.  Where am I going wrong?

I have:
Toshiba Satellite A105-S4074 Notebook
Intel Centrino Duo Processor
Toshiba MK1234GSX Internal HDD (120 GB)
Travelstar IC25N040 ATMR04-0 USB External HDD (from old Gateway notebook)
Matshita DVD-RAM UJ-841S CD/DVD drive
It seems, although, you have set the BIOS to boot from CD it is failing.
The boot sector on a bootable CD is generally missed if the head of CD drive needs cleaning. If you have any other bootable CD which has worked earlier you can try to confirm this. If head cleaning is required it won't boot as well.

Please clean the head of the drive and try again.

kagashe

---

### Post by Captain Obvious on 2007-04-25
> **kagashe said:**
> It seems, although, you have set the BIOS to boot from CD it is failing.
The boot sector on a bootable CD is generally missed if the head of CD drive needs cleaning. If you have any other bootable CD which has worked earlier you can try to confirm this. If head cleaning is required it won't boot as well.

Please clean the head of the drive and try again.

kagashe

i think i'm completely retarded.  i was burning the file as a data disc in Sonic Record Now, so now i'm using a special burning program for ISO files. we'll see how it works out.

---

