---
title: "Lucid alternate install doesn't detect SATA chipset"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Centaur5 on 2010-03-25
When trying to do an alternate install of Ubuntu 10.04 Lucid using a daily build as of the date of this writing it fails to find my hard disk.  This chipset has been on motherboards I've been using for a long time with Jaunty and Karmic but now it fails to work in Lucid.  I was able to successfully install with the desktop CD but that is not my desired method for future installs.  The motherboards I'm using are Asus M4A77D and M4A78L-M which use the AMD 780G chipset.  Here is the lspci of the SATA controller:

00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]

---

### Post by Mark Phelps on 2010-03-25
Lucid is not yet released, and all beta-related issues and questions should be posted to the correct forum: Development & Programming, Lucid Lynx Testing.

I'm requesting the Mods to move this thread accordingly.  Look for responses there.

---

### Post by dabl on 2010-03-25
Try setting the SATA mode in BIOS to "Legacy IDE" or whatever the legacy option is.  If using that mode gets you past the installation, then you can probably set it back to AHCI afterward, and it should boot and run fine.

---

### Post by Centaur5 on 2010-03-25
I originally had the motherboard in IDE mode but found a previous forum from a couple years ago where somebody told a guy to do AHCI then it worked.  Unfortunately, neither way worked for me.  I was just wondering if this is a bug that might work itself out or if they really made it so you have to manually add the driver.  The text installer when it doesn't see a drive asks for the driver to be selected and gives the option to add one from a removable device.

---

### Post by Centaur5 on 2010-03-25
Well I thought that maybe I was doing something wrong but just discovered this is a bug that is supposed to be fixed in beta 2.  The bug can be found at [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/546929](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/546929)

---

