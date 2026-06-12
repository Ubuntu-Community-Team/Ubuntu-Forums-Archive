---
title: "Problem with booting XP after upgrade to 10.04"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by 3saul on 2010-05-01
After going through the upgrade (alternate cd) I now can't boot into XP, even though it's in the GRUB2 menu.

I have fixed up the boot sector as described at [this site]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

Attached are my results from the boot info script

SDA1 is XP
SDA3 is 10.04

sda3 has this strange error:
> Grub 2 is installed in the boot sector of sda3 and looks at sector 66800445 of the same hard drive for core.img, but core.img can not be found at this location.

---

### Post by oldfred on 2010-05-01
After you ran the fix from meierfra's site did that not let you boot? Did you run a sudo update-grub just to make sure the links are refreshed?

Somewhere in the install you managed to install grub everywhere. I should only be in one (maybe two) drive MBR's. Not in any partitions unless you are doing very advanced booting and know that it may break if you do install it to a partition. Having it in partitions (other than windows) will not cause any problems. In the windows partition it overwrites the windows 2nd part of boot process, whcih it looks like you have repaired.

---

### Post by 3saul on 2010-05-01
I did update-grub after fixing the boot sector. I can boot into 10.04, but not XP - just sits there with a blinking cursor.

What you describe is exactly what happened, grub installed on ALL of my drives. What else can I do now???

> **oldfred said:**
> After you ran the fix from meierfra's site did that not let you boot? Did you run a sudo update-grub just to make sure the links are refreshed?

Somewhere in the install you managed to install grub everywhere. I should only be in one (maybe two) drive MBR's. Not in any partitions unless you are doing very advanced booting and know that it may break if you do install it to a partition. Having it in partitions (other than windows) will not cause any problems. In the windows partition it overwrites the windows 2nd part of boot process, whcih it looks like you have repaired.

---

### Post by oldfred on 2010-05-02
If testdisk did not repair the windows boot sector perhaps the windows tools will.

To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

BOOTCFG  /rebuild

Check that windows boots, then you can reinstall grub.

IF that does not work post a new run of results.txt but be sure to put code tags (highlight & # in menu as you edit) around the entry.

---

