---
title: "Installation help"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by kinghippy on 2008-03-30
Ok, so this is a weird problem. There is no previous operating system on this computer, so maybe I'm just doing something wrong. I've always installed with Windows already installed, but this time I built the computer myself.

So here's what happens: The computer isn't booting from the CD-ROM drive. What's weird about that is that when I go into the BIOS setup screen, the computer sees the CD-ROM device and it is scheduled as the primary boot device.  So it schedules the boot from the CD-ROM, but it just doesn't actually do it. And that's really the most important part. If it's not going to boot from the CD-Rom drive, I have no clue how to install Ubuntu. :(

---

### Post by Shazaam on 2008-03-30
Since you say your bios sees the drive we can rule that out. BUT, the drive could be defective.
Two things to try.....
1. Burn the Ubuntu iso as SLOW as you can. Try it at 4x.
2. Re-download the iso again or order a cd from canonical.

P.S. Do you hear the cd spin up?

---

### Post by kinghippy on 2008-03-30
I am using an ubuntu disk that they provided. I have installed from it before without problems.

I can't hear it spinning. The indicator light on the device lights up as soon as I turn the machine on, but not when it's supposed to be booting. All I keep getting is "Disk boot failure, insert system disk and press enter"  This is what I get even after I press F8 to load the boot menu and manually tell it to boot specifically from the CD-ROM. If it were a device failure, you would think that the computer wouldn't even detect it.

---

### Post by kinghippy on 2008-03-30
My mistake: when I manually attempt the boot from the boot menu, the indicator light on the device does come on, but I still don't hear it spinning

---

### Post by Shazaam on 2008-03-30
Hmmm.I have 2 cd drives and I can hear them spin up. Also when you get the bios disk boot failure error it means you are trying to either boot an empty hard drive or you are using a non-bootable cd (for example a music cd).
Sounds like a hardware or bios problem. Check the wiring to the drive and look through the bios again to make sure the drive is correctly hooked up. For a temporary check if you have another working drive sitting around you might try swapping it out.

---

### Post by pietjanjaap on 2008-03-30
If you have sata drive, check your bios if you have a setting like "native", here you can choose 2 or 3 things, choose native.

---

