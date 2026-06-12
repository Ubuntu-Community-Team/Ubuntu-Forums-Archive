---
title: "Ubuntu 18.04 suddenly giving Non-System disk or disk error"
date: 2019-03-20
forum: Installation &amp; Upgrades
---

### Post by graywolfit on 2019-03-20
I have an HP Gen8 Microserver configured as outlined below.  The system has been installed with Ubuntu 18.04 for the past several months and has been running our NVR system.  This morning, the system was in a non-responsive state.  After a hard reboot, it boots to a Non-System disk or disk error screen.  I have successfully booted off of a Live 18.04 USB and I can see the OS drive and all data etc... appears intact.  I attempted a Boot-Repair which said it completed successfully but still boots to the same error.

System - HP Gen8 Microserver - BIOS (Not UEFI)
Memory - 16GB RAM
Boot/OS - 120GB SSD SATA drive (entire drive used for OS)
Add on HP 222 RAID controller with 4X 6TB WD Purple drives.  (3X RAID 5, 1X Hot Spare) used for camera storage.

Any help is greatly appreciated as this was/is a production camera server that is now down.

I attempted to add an attachment of the boot-repair log output but the attachment system never would show the .txt file I had.  When I attempted to paste it within this posting with the # for Code and tried to submit, it gave an error about length of the post and then gave me a blank form that I had to fill again when I went back to the form.  If someone can tell me how to post that data for review, I will do so.

Thanks again.

---

### Post by graywolfit on 2019-03-20
I have resolved it.:)    So, since the Microserver was booting off the Live USB with no issue, I decided to attempt to boot the original SSD via USB.  So, I connected the SSD to an USB to SATA converter and plugged into the on board USB port and booted the server.  IT BOOTED.:)  This lead me to believe that the issue is with the boot selection/order of the Microserver and the SATA interface.  

So, I went through the HP B120i controller interface configuration utility and found that the SATA drive was seen but not associate/assigned to the controller any longer.  To resolve this, I added the drive back to the controller (creating an RAID 0 Array) and then set it as the bootable device on the controller.  Rebooted and it is now seen as the boot device and the OS booted normally.  

All appears to be back to normal and operating.  Not sure what/why the existing boot device would somehow disassociate with the controller but it did.

---

