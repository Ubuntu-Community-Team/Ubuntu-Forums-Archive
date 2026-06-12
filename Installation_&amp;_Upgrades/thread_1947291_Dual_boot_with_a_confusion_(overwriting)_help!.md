---
title: "Dual boot with a confusion (overwriting) help!"
date: 2012-03-26
forum: Installation &amp; Upgrades
---

### Post by coyoteboy on 2012-03-26
I'm attempting to install Ubuntu onto a system that currently is a dual-boot with XP and W7. I really need the XP boot to remain alive, I don't care for the W7 at all. During the installation process Ubuntu asks if it can overwrite W7 but mentions nothing of XP. As I wanted to be sure i didn't overwrite the boot info for XP as well as W7 I went down the custom route but then I'm faced with some questions I can't answer, namely:

1) The W7 loader is installed on a drive (sda) that is the XP drive, not the one with the W7 installation (sdc). I want to overwrite the W7 (sdc1) completely but don't want to stop the XP boot option. Can I allow the standard installation to proceed to wipe the W7 installation and take control of the BR, or do I have to go through the customised process, if so...

2) What's the best way of handling the boot loader and data locations?

Cheers all, no rush - side project!

11.10 FWIW.

---

### Post by kc1di on 2012-03-26
> **coyoteboy said:**
> I'm attempting to install Ubuntu onto a system that currently is a dual-boot with XP and W7. I really need the XP boot to remain alive, I don't care for the W7 at all. During the installation process Ubuntu asks if it can overwrite W7 but mentions nothing of XP. As I wanted to be sure i didn't overwrite the boot info for XP as well as W7 I went down the custom route but then I'm faced with some questions I can't answer, namely:

1) The W7 loader is installed on a drive (sda) that is the XP drive, not the one with the W7 installation (sdc). I want to overwrite the W7 (sdc1) completely but don't want to stop the XP boot option. Can I allow the standard installation to proceed to wipe the W7 installation and take control of the BR, or do I have to go through the customised process, if so...

2) What's the best way of handling the boot loader and data locations?

Cheers all, no rush - side project!

11.10 FWIW.

Tell the installer which drive you want to erase for Ubuntu , then allow it to do it's thing it will install and create and new Master boot recored (MBR) and should find your xp install without problems.
[B]
But as Always I recommend you back up any important files cause things do go wrong at times.  [/B]

I would partition SDC so that you have 10 gigs for ubuntu / and about 20 or more gigs if available for /home partitions. 

you can do that in the installer on the screen that say partitions by choose the something else at the bottom of the list.
just make sure you don't touch sda.

good luck

---

### Post by Hakunka-Matata on 2012-03-26
HI, The safest approach at this point would be to boot the computer to the LiveCd (your install disc), choose try Ubuntu, and once there launch the Ubuntu Partition Editor, gparted.  Use it to set up your drives and then install it using the "something else" partitioning scheme.  It'll be much easier and safer.  Some Releases of Ubuntu have notoriously dangerous partitioning quirks, hence the recommendation is to use gparted.
good luck

---

### Post by oldfred on 2012-03-26
A bootable Windows partition must be a primary NTFS partition with the boot flag. If one install is in a logical partition you cannot delete the one in the primary partition and still use the one in a logical partition.

So is the XP partition the boot partition? If so you will be fine, but may have to repair the XP install as Windows 7 moved its boot files into your XP partition and took over booting. But if Windows 7 is the boot partition the XP boot files are in the Windows 7 partition.

Have you used all four primary partitions? Often the Ubuntu installer cannot do an auto install if all four primary partitions are used or it cannot move other partitions around if too many exist. It then only gives options of totally erasing or using manual install or Something Else. I prefer to partition in advance with gparted. But if changing the size of the Windows 7 partition use the Windows 7 tools to edit and reboot several times to make sure it has run chkdsk and other fixes to fully recognize the new size.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

