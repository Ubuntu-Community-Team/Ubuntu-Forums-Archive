---
title: "How to hide grub after removing Windows from dual-boot config"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by potatan on 2010-08-27
Hi,

I installed Ubuntu in dual boot with XP on a friend's netbook.  She's happy to stick with Ubuntu, so now I want to remove all traces of XP including the grub stuff.  I can delete the XP partition and resize Ubuntu, but what do I need to do with Grub, to:

1. remove the option to select Windows
2. remove the text-based boot completely so the machine boots straight into Ubuntu without any of the "scary" text-based menus

As it's 10.04, I'm not familiar with Grub2 to try this unaided, and all the searches I perform seem to return results to do with getting rid of grub completely.

Thanks in advance

p.s. the automated transfer of files and settings from Windows was excellent - it included favourites and windows desktop wallpaper, I was pleasantly surprised having never used it before

---

### Post by Rubi1200 on 2010-08-27
> **potatan said:**
> Hi,

I installed Ubuntu in dual boot with XP on a friend's netbook.  She's happy to stick with Ubuntu, so now I want to remove all traces of XP including the grub stuff.  I can delete the XP partition and resize Ubuntu, but what do I need to do with Grub, to:

1. remove the option to select Windows
2. remove the text-based boot completely so the machine boots straight into Ubuntu without any of the "scary" text-based menus

As it's 10.04, I'm not familiar with Grub2 to try this unaided, and all the searches I perform seem to return results to do with getting rid of grub completely.

Thanks in advance

p.s. the automated transfer of files and settings from Windows was excellent - it included favourites and windows desktop wallpaper, I was pleasantly surprised having never used it before

1. remove XP and run```
 sudo update-grub
``` the option will be gone

2. from the tutorial by drs305:
> **GRUB_HIDDEN_TIMEOUT=0**   [ [COLOR=DarkRed]Note: This setting only applies to computers with only a single operating system.[/COLOR] ]The  hidden timeout option allows a screen to be displayed without the Grub 2  menu, awaiting input from the user for a given number of seconds. It is  available to single-OS computers - if multiple OS's are known to Grub  2, this option is bypassed. 
**On single-OS computers:**
[LIST]
[*]The menu will be hidden unless the  user adds a # symbol to the beginning of this line ( #  GRUB_HIDDEN_TIMEOUT=0 ) and the GRUB_TIMEOUT value is greater than 0.
[*]If a background image is designated in 05_debian_theme it will be  displayed rather than a blank screen during a hidden menu timeout.
[*]**For integers greater than 0**:
[LIST]
[*]The system will pause without displaying a menu for the designated number of seconds. If the user does not press the *SHIFT* key during the timeout the system will then boot the default OS/kernel.
[*]If the user presses the *SHIFT* key to display the menu, the  menu will be displayed for the number of seconds designated by the   GRUB_TIMEOUT value unless the user again intervenes.
[/LIST]
 
[*]With a value of **0**:
[LIST]
[*]Unless the user intervenes, the system will boot the default OS/kernel with only a slight delay. No menu will be displayed.
[*]The user may force displaying the menu as the computer boots by holding down the *SHIFT*  key.
[/LIST]
 
[/LIST]
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

You can edit this:
```
sudo gedit /etc/default/grub
``` and find that line and set the integer to whatever you want.
If you have any further questions, feel free to ask.

---

### Post by potatan on 2010-08-27
Actually - there seems to be no (easy) way to recover the partition allocated to XP.  I have deleted it, but the Ubuntu EXT3 and swap partitions are part of an extended logical drive, so I can't resize them to use the freed up XP space that I deleted with gparted.

Any ideas?

---

### Post by oldfred on 2010-08-28
I do not like moving partitions left as you have to copy & verify the entire thing. Ofter very slow. But you can move the extended left then move the linux partition left.

But I would just use the old XP partition as /home or just as a data partition.

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
You do not have to have multi boot to have a data partition:
How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

