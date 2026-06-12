---
title: "[SOLVED] Want to dual-boot windows and ubuntu, but windows will not recognize hard dr"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by Lacent on 2008-05-12
Ok, so I have had this problem for a very long while now, and I would like to get it fixed. I have tried several things that I have found on the net, but to no avail. I have a legit Windows XP pro disk that I pop in my computer. Every time i start it, it goes through the normal setup stuff, until I press enter to install. Once I do, it brings up an error that says I do not have a hard drive. I figured this was a format problem, with windows not recognizing the format that my drive was in. This being said, I popped in the gparted live cd, and made a partition as ntfs, as well as one with fat32. Neither of these worked, since it gave me the same problem. Then, I started from scratch. I put the DBAN (derik's boot and nuke) cd in, and totally wiped my hard drive. Still didnt work. I have followed the guides out there to have ubuntu and then install windows, but these only tell you to go the gparted route, which I have already tried. I love Ubuntu, and switched to it cold-turkey about a year ago, and have loved every minute since. However, I would like to run some of my windows apps (games). Also, I have tried to run a virtual windows, which I am still working on, however, I would prefer to have my windows on a partition. Thanks alot for the help that you give, not only to this question, but all of the newb questions, ubuntu forums!

---

### Post by anon98sz on 2008-05-12
Are these SATA or SCSI drives?  Are you getting to the point where it shows you the current partitions, or is it reporting that there are no compatible disk drives in the system?

It sounds like you need the driver disk for your hard drive controller.  When you first boot off the CD it says to press F6 to load additional drivers.  Unfortunately XP and earlier can only load these drivers from a floppy drive.  Another possibility is that in the BIOS, if the drives are SATA, you can set it to legacy mode.  After you install a fresh copy of XP and install the proper drivers for you controller then you may be able to turn off the legacy mode.

Hope that helps.

---

### Post by Tomatz on 2008-05-12
You need to create a fat32 partition for windows to recognise make sure you leave enough free space for ubuntu (windows cant recognise EXT3 the linux filesystem).

Use the gparted live cd to do this:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

[COLOR="Red"]**CAUTION you run the risk of borking your system, use wisely**[/COLOR]

Windows will eat your bootloader (grub) when you install it. If you cant fix this after you install xp post back. ;)

---

### Post by Lacent on 2008-05-12
> **Tomatz said:**
> You need to create a fat32 partition for windows to recognise make sure you leave enough free space for ubuntu (windows cant recognise EXT3 the linux filesystem).

Use the gparted live cd to do this:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

[COLOR="Red"]**CAUTION you run the risk of borking your system, use wisely**[/COLOR]

Windows will eat your bootloader (grub) when you install it. If you cant fix this after you install xp post back. ;)


Well, if you would read my post, you would see that I already tried that.

---

### Post by Tomatz on 2008-05-12
> **Lacent said:**
> Well, if you would read my post, you would see that I already tried that.


Sorry

The only other thing it could be is that your Hdd isnt set up as primary (**not** first boot device) drive in the bios.

;)

---

### Post by CitrusOrange on 2008-05-12
Check your cables and pins on the drive. Make sure the hard drive is set as "Master" and not "Slave". CE or Cable Select also works but it's better to set it as Master.

Once you have made sure your hard drive is correctly wired, go into bios and have your boot priority set to CDROM first then HDD0 second.  Make sure that the computer sees the hard drive as master in Bios before going any further.

Once you got that all done, pop in your installation CD and then install Windows XP first and make sure you use FAT32 Format.
I have no idea if NTFS can be resized.

Once Windows is in, pop in your Ubuntu install CD and during the install process, choose the option to resize your partition. I usually split it in half equally.

This is the way I've been doing it for years and I've never had an issue with it. I also let GRUB boot loader let me choose between windows and ubuntu.

However, it's easier just to buy a second hard drive and put Windows on the first one and Ubuntu on the second one. I use this method when ever possible. This method skips the annoying partition resize nonsense.

---

### Post by Lacent on 2008-05-12
> **anon98sz said:**
> Are these SATA or SCSI drives?  Are you getting to the point where it shows you the current partitions, or is it reporting that there are no compatible disk drives in the system?

It sounds like you need the driver disk for your hard drive controller.  When you first boot off the CD it says to press F6 to load additional drivers.  Unfortunately XP and earlier can only load these drivers from a floppy drive.  Another possibility is that in the BIOS, if the drives are SATA, you can set it to legacy mode.  After you install a fresh copy of XP and install the proper drivers for you controller then you may be able to turn off the legacy mode.

Hope that helps.

This was exactly what I needed. Although on my computer (IBM Thinkpad t60p) it wasnt called legacy mode, it was called configurable mode or something like that. Thanks for the help!!!

---

