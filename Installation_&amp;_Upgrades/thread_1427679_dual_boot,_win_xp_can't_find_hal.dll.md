---
title: "dual boot, win xp can't find hal.dll"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by kshunter on 2010-03-11
Hi, 

I installed Ubuntu 9.10, on a system that already had Windows XP installed and working fine. When I select Windows XP from the boot option, it says:

"Windows could not start because the following file is missing or corrupt:
  <Windows root>\system32\hal.dll.
  Please re-install a copy of the above file."

I suspect that this has something to do with the fact that Windows is installed on a SATA drive, E: in windows, or sdc2 in Ubuntu. I had to use a 3rd party RAID driver from floppy during the Windows installation. 

In Ubuntu I can see the file is there in the windows\system32 folder and it does not appear to have been modified. 

I should mention that when I installed Ubuntu, something went wrong with Grub and the screen would display "Grub Loading..." for at least 20 minutes before booting. I tried reinstalling grub2 to no avail, and I eventually downgraded to grub 0.97 which resolved the issue. 

Still, I don't think that's the problem because I tested loading windows when Grub2 was still installed, (by editing the grub menu so that it wouldn't automatically load Ubuntu) and it didn't work then either. 

My menu.lst entry for windows: 
---------
title        Windows 95/98/NT/2000
root        (hd0,0)
makeactive
chainloader    +1
---------

My boot.ini on what would be the C:\ drive: 
---------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(2)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(2)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin
---------

**Edit:  **When Windows installs a "3rd Party RAID driver" so it can read the SATA drive, where does the driver go? Does it go on the boot sector of the first hard drive (which is IDE)? And in that case, does Ubuntu write over the SATA driver? Is there some way to get GRUB to load a driver for the SATA drive before it tries to load windows? 

Thanks in advance for any help.

**Edit: **I ended up re-installing Windows. Probably I could have gone into Windows Recovery Console and fixed boot.ini, but the custom build Windows CD I had on hand didn't seem to have the recovery console. 

I believe the file I had above wasn't even actually the copy of boot.ini that Windows is using. When I reinstalled it disappeared. 
As an aside, since I did not remove the old installation of Windows, when I installed again it installed to \WINDOWS.0. and created a boot menu with two entries, one for the old installation and one for the new. From the new installation, I edited the boot menu entry to point to the correct partition, and I'm back to windows the way it was. 

Now to try to restore grub.

---

