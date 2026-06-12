---
title: "Error 15 when using Windows installer for Ubuntu 8.04"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by Azroen on 2008-05-05
I tried to install Ubuntu 8.04 onto my computer's 2nd hard drive but had some problems.  The main OS is Win XP Pro.  I put a second hard drive into it, reformatted it, and then used the Ubuntu 8.04 install CD (downloaded it and burned it as a disk image) to install Ubuntu using the Windows installer.

Everything installed fine and I received the message that I needed to reboot to finish the install.

I rebooted and I got the program manager to choose the OS.  Windows XP Pro was listed as was Ubuntu.  I selected Ubuntu and fairly quickly I was given the message: "Error 15: File not found."  I had the option to dropping into GRUB.

At this point I'm lost.  :)

Some things that may be related to this:

1. As mentioned, I selected the installer to install on the 2nd hard drive. Did I need to do anything further?

2. Spybot Search and Destroy was running while I installed Ubuntu (I frankly forgot to turn it off).  When I rebooted and Ubuntu would not start, I rebooted into Win XP Pro (which came up fine) and I had a spybot pop up that said something to the effect of, "start up change denied."  It came up and disappeared quickly though, so I didn't copy it down.  Might this have prevented whatever start up file that needed to be edited from being edited?

Any suggestions?  Turn off spybot and reinstall?  Do something else?  I'm lost. :(

---

### Post by Azroen on 2008-05-05
I uninstalled (control panel->Add/Remove Programs), turned spybot and AVG off, and reinstalled.  Rebooted and upon Spybot's startup it again gave me a denied message for the bootexec file.  I went into Spybot's blacklist and removed this entry, uninstalled Ubuntu again and reinstalled again.  This time when I rebooted into Windows I received a message asking to permit/block the bootexec change and I accepted it.  Rebooted and selected Ubuntu and I received the same error:

Error 15: file not found

find -- set-root -- ignore-floppies /ubuntu/install/boot/grub/menu.lst

***

Trying to install Ubuntu 8.04 on the 2nd hard drive of a Win XP Pro sp3 machine.

Any ideas?

---

### Post by logos34 on 2008-05-06
reinstall but this time do not use the wubi/windows installer method.  Put it on its own ext3 partition on the 2nd drive.  When you get to the grub bootloader options screen choose to put it on a floppy (fd0) and boot from that when you want to go into linux

---

