---
title: "location of grub?"
date: 2012-01-27
forum: Installation &amp; Upgrades
---

### Post by paulgault on 2012-01-27
the kids keep hogging my computer so i built a spare machine from old bits which have been either donated or bought for very little from ebay.

the lubuntu install works just fine and the thing is pretty impressive when this is booted.

the problems are all windows related! aaarrrggghhhh!!!!

both lubuntu and XP have their own separate hard drive.

the bios is set to boot the disc where lubuntu is installed, where grub2 is located and passes control over to whatever OS is selected.

it's a bit baffling but both operating systems work fine with this arrangement until one day XP decides to stop playing ball and will restart as it's loading up. when it does this grub2 loads up again (as it should) and when selecting XP to have another go at loading up it tells you that windows didn't load properly last time and gives you the option of either trying a normal boot or going into safe mode (never really understood the point of safe mode!). 

after a bit of messing i found that if i change the boot order in the bios to load from the drive with XP on it (and no grub, just a standard MS MBR) it will sometimes boot windows ok and once windows has booted normally it carries on booting properly via grub2 when i've put the bios  back to booting from the lubuntu/grub2 drive.

it then works fine for a while, until it doesn't and then i have to go through the whole thing again. sometimes i have to open up the case and physically disconnect the lubuntu/grub2 drive before XP will boot normally.

anyone know what's going on here and does it make any difference which drive i put grub2 on?

thanks.

---

### Post by SteveDee on 2012-01-28
> **paulgault said:**
> ...XP decides to stop playing ball and will restart as it's loading up. when it does this grub2 loads up again (as it should) and when selecting XP to have another go at loading up it tells you that windows didn't load properly last time and gives you the option of either trying a normal boot or going into safe mode (never really understood the point of safe mode!)....

From this statement it sounds like it is purely a Windows problem. (Safe mode just allows you to boot Windows without drivers which may be causing problems). So the next time it follows this pattern, I'd suggest selecting Safe Mode and seeing if it will load Windows. You can then force a hard disk check.
In fact I'd load Windows and do a disk check (on the Windows disk) anyway.

From Lubuntu you could run the Disk Utility (if not installed, open Synaptic and search for gnome-disk-utility). This should show both HDD and help diagnosis.

---

### Post by oldfred on 2012-01-28
I also agree it sounds like a Windows issue.

It seems that Windows may be running chkdsk? That is one reason it wants to use safe mode as it cannot run chkdsk from a fully mounted system.

Are you writing from Ubuntu directly into the XP NTFS partition or hibernating in XP and doing anything from Ubuntu in the NTFS partition. Windows often does not like others messing with its system partition. If you want to share data a separate NTFS partition is a better way.

---

