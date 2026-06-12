---
title: "Update HP Pavilion dm1z BIOS"
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by -Shuji- on 2011-09-18
I have a Pavilion dm1z that needs a BIOS upgrade from F.05 to F.13.  The only available BIOS update from HP Support is an executable WinFlash (sp54026.exe).  Is there another way to update my BIOS other than installing Windows 7 64-bit on another partition and running the installer there?

Shuji

---

### Post by Frogs Hair on 2011-09-18
First make sure the bios has updates that benefit your computer / hardware . If it only includes hardware support for something you will never use don't bother . If it is an .exe you may have to install Windows . Using Wine to run bios update software has been discussed , but I have no idea if it would work .

I updated my dual boot last week but mine flashes from a floppy . All I had to do was , download , extract , save to my external floppy and enter the bios screen at boot and follow the instructions in my mobo manual .

---

### Post by -Shuji- on 2011-09-19
> **Frogs Hair said:**
> First make sure the bios has updates that benefit your computer / hardware . If it only includes hardware support for something you will never use don't bother . If it is an .exe you may have to install Windows . Using Wine to run bios update software has been discussed , but I have no idea if it would work .

I updated my dual boot last week but mine flashes from a floppy . All I had to do was , download , extract , save to my external floppy and enter the bios screen at boot and follow the instructions in my mobo manual .

Frogs,

I'm having a problem disabling WOL which consumes battery even when the laptop is off.  Although the BIOS update did not specifically say it will fix that problem, I felt like I needed to upgrade to fix the fan noise issue.

I realized how risky it is to run the BIOS update utilty from Wine so I just decided to install Windows 7 on another partition and from there, run the update.  I had no other choice since HP does not provide or support BIOS update from DOS. To other Ubuntu users,  I would recommend this lengthy but safe method of flashing the BIOS.  Thanks for your advice.

Shuji

---

### Post by Frogs Hair on 2011-09-19
> I realized how risky it is to run the BIOS update utilty from Wine so I just decided to install Windows 7 on another partition and from there, run the update. I had no other choice since HP does not provide or support BIOS update from DOS. To other Ubuntu users, I would recommend this lengthy but safe method of flashing the BIOS. Thanks for your advice.

I have an Asus board and they currently have three methods that I kmow of for bios update . My board still uses easy flash though it is not very old.

---

