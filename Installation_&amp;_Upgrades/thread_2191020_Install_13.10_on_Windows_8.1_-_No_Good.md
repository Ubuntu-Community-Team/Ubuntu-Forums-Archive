---
title: "Install 13.10 on Windows 8.1 - No Good"
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by richramik on 2013-11-30
Have an HP Pavilion, Windows 8.1, 2Tb machine.  Tried installing 13.10 using wubi.  Install seems to work. When it restarts and gets to the OS Selection, I select Ubuntu.  Screen goes black then comes up with an error dialog.  Along with other dribble, this is what I get.

\ubuntu\winboot\wubildr.mbr
Status oxcooooo7b
Required file is missing or contains errors

I even tried to install 12.04.3 but got the same messages.

Bottom line, I want to install Ubuntu and replace Windows 8.

Thanks,
Rich Ramik

---

### Post by coffeecat on 2013-11-30
Well...

> **richramik said:**
> Bottom line, I want to install Ubuntu and replace Windows 8.

If that's the case, you shouldn't be trying to install with wubi. A wubi install is installed to a pseudo-partition inside the Windows filesystem. It's intended only as a tryout for those who wish to retain Windows. And the reason you are experiencing problems is that wubi does not work in Windows 8.

If you want to get rid of Windows entirely and replace it with Ubuntu, you need to download the Ubuntu ISO, prepare a bootable DVD or USB and use the live session to repartition your hard drive and install Ubuntu. With a Windows 8 machine, you'll have a UEFI BIOS with secure boot, so there are some things to consider:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by richramik on 2013-12-01
Thanks coffcat for the information.  I ended up funding my way to "http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html" and downloaded to the desktop the turn off "bat" file.  That did the trick.  I loaded the dvd and then restarted the system.  This is where I don't quite remember which option I used.  During the boot-up, I got the the settiongs menu and I'm guessing set the boot sequence to read from the DVD.  It did ask me what course of action I wanted to take.  Obviously choose load Ubuntu.  In that process I cleaned my hard drive and strarted loading 13.10.  All is happy in Mudville tonight as I'm respondig from a Ubuntu system.  It took a bit of time to do this because I explored several of the options presented and had company visiting.  Thanks again.

---

