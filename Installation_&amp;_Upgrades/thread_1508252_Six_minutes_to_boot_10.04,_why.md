---
title: "Six minutes to boot 10.04, why?"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by JohnnyB98604 on 2010-06-12
I've just installed Ubuntu 10.04 LTS on my netbook (Toshiba NB205) and it takes nearly six minutes to boot.  It gets past the BIOS screen just fine.  Then it goes to a black screen with the cursor blinking in the upper left-hand corner of the screen for something like 00:05:50.

I've let Ubuntu load all updates after in the installation and I've gone through the BIOS settings...I don't see anything in there that would effect it but...I'm not that savvy.

Any thoughts or suggestions would be very helpful.

Oh yes...by looking at the lights on the netbook it doesn't appear that there's anything going on with the HDD.  Occasionally, it gives a little flicker but it's not like it's running the whole time it's trying to boot.

---

### Post by JohnnyB98604 on 2010-06-12
> **JohnnyB98604 said:**
> I've just installed Ubuntu 10.04 LTS on my netbook (Toshiba NB205) and it takes nearly six minutes to boot.  It gets past the BIOS screen just fine.  Then it goes to a black screen with the cursor blinking in the upper left-hand corner of the screen for something like 00:05:50.

I've let Ubuntu load all updates after in the installation and I've gone through the BIOS settings...I don't see anything in there that would effect it but...I'm not that savvy.

Any thoughts or suggestions would be very helpful.

Oh yes...by looking at the lights on the netbook it doesn't appear that there's anything going on with the HDD.  Occasionally, it gives a little flicker but it's not like it's running the whole time it's trying to boot.

More information:
It's not booting.  I've left it for over an hour and it's still just flashing at a cursor.  One peice that I left out was Windows 7 Starter.  It was running Win7 Starter before the switch...my step-son tried to put windows XP on it but the winXP installation failed stating that there was no drive recognized...Windows 7 Starter will STILL install without issue (other than it's a crappy OS) so I'm wondering if the Win 7 installation has done "something" to the drive.

so, my search will continue on other forums and I'll post any results here...I'm sure I'm not the only person to replace win7 with Ubuntu...

---

### Post by oldfred on 2010-06-12
Windows installs will overwrite the MBR, so depending on what you have done it may have part of a windows install?

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

IF reinstalling grub does not work, run this script.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

If you get it to the menu, use e for edit and remove splash & quiet so you can see each line as it boots. That may help tell what is so slow. The same info is in the log files. Use system, adminstration, log view viewer.

---

### Post by JohnnyB98604 on 2010-06-15
Figured it out, than you Ubuntu forums!!!

It was a BIOS setting.  The SATA setting for the Toshiba NB205 needs to be changed to "Compatibility" instead of "AHCI" (which is the default).

Once this change was made, boot times went from several minutes (or never) to just under a minute.

---

