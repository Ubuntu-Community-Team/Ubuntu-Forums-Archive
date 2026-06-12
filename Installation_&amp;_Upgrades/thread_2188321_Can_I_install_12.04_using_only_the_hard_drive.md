---
title: "Can I install 12.04 using only the hard drive?"
date: 2013-11-16
forum: Installation &amp; Upgrades
---

### Post by skitter on 2013-11-16
I'm trying bring an old Compaq Presario SR2150NX back to life, but I'm getting the infamous '[FONT=arial]Unable to find a medium[/FONT][FONT=arial] containing live[/FONT][FONT=arial] file system' error. The BIOS for this PC doesn't support booting from USB, and is the most recent version Compaq offers.  I've tried installing with only a SATA hard drive, and with only an IDE hard drive, but get the same error.  I tried setting the (IDE) DVD drive to both master and slave (using the correct cable position) and still have the error.[/FONT] So that's the back ground.    I do have another perfectly fine machine, and I also have a nifty SATA / IDE to USB adapter. What I'd like to do is remove the Presario's hard drive and attach it to my good machine using the SATA / USB adapter. Is there a way to copy the installer and bootloader on to that drive, then put the drive back in the Presario and run the install?  Edit- decided I really don't have much to lose, so I tried this:  Removed all drives (CD and hard) from the Presario. Attached an IDE drive to my USB adapter and attached that to my good PC. Ran the startup disk creator.  The install runs fine. Remove the drive from the USB adaptor and attach it to the IDE cable on the Presario. Drive jumper is set to master, and it's on the last cable position.  BIOS recognizes the drive, but at bootup, it throws an error "Primary slave ATAPI incompatible F2 to continue" (there is only one drive attached, no DVD, floppy, etc). After pressing F2, it looks like the O/S tried to load, but I then get "Reboot and select proper boot device"  Edit 2-   Perhaps I'm not going about this the best way.  I'm certianly open to suggestions if there's a better way to get Ubuntu running on this old box.  Edit 3-  Got it working.  Downloaded the 12.04 ISO again. It wouldn't fit on a CDR, so I burned it to a DVDR, and now the install is working. Not sure if there was a problem with my old CD, or if there's a newer 12.04 ISO that addresses this issue.

---

### Post by Bucky Ball on 2013-11-16
*Thread moved to **Installation & Upgrades**.*

You might have more luck here. 

Installing Ubuntu on the drive using another machine then connecting it up to the dead one was what I was going to suggest. It looks like it is seeing the drive as a slave, though. Can you flip the jumper or check the BIOS to see how the BIOS is reading that drive (as second boot device, perhaps, but there isn't a first so causing confusion?).

---

### Post by skitter on 2013-11-16
I solved the 'F2 to continue' problem- in the BIOS, drive 2 was set to none, but when I entered the submenu, it was set to CD.  I changed the submenu to none, and now no longer see that warning.   That said, boot up is still bombing out with the "Reboot and select proper boot device" error.

---

