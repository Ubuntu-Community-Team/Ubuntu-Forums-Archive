---
title: "Grub Problem after upgrade to 11.04"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by bfromcolo on 2011-10-29
I have been dual booting 10.10 and Win 7 for months with no issues.  Today I ran the upgrade to 11.04, on reboot I got:

error: symbol not found" 'grub_env_export'.
grub rescue>

The system has 3 drives, Ch 0 Linux, Ch 2 Windows, Ch 3 storage.
The system had been setup to boot off Ch 0 where GRUB was installed by a clean build of 10.10.

For whatever reason with the install of 11.04 Grub has been installed on the Ch 2 drive, over writing the Windows boot loader.  Setting the system to boot off Ch 2 works fine for both Windows and Ubuntu.  But I would prefer to have Grub back on Ch 0 and to restore the Windows boot loader on the Windows disk. This way when the grand kids are messing with my computer I can set it up to boot Windows directly and not present a list of choices when I want.

I can fix the Windows disk but how do I get Grub installed where I want it.

Thanks

---

### Post by raja.genupula on 2011-10-29
> **bfromcolo said:**
> I have been dual booting 10.10 and Win 7 for months with no issues.  Today I ran the upgrade to 11.04, on reboot I got:

error: symbol not found" 'grub_env_export'.
grub rescue>

The system has 3 drives, Ch 0 Linux, Ch 2 Windows, Ch 3 storage.
The system had been setup to boot off Ch 0 where GRUB was installed by a clean build of 10.10.

For whatever reason with the install of 11.04 Grub has been installed on the Ch 2 drive, over writing the Windows boot loader.  Setting the system to boot off Ch 2 works fine for both Windows and Ubuntu.  But I would prefer to have Grub back on Ch 0 and to restore the Windows boot loader on the Windows disk. This way when the grand kids are messing with my computer I can set it up to boot Windows directly and not present a list of choices when I want.

I can fix the Windows disk but how do I get Grub installed where I want it.

Thanks

Hi look my signature for Grub Recovery. I am sure its gonna help you.

All the best.

---

