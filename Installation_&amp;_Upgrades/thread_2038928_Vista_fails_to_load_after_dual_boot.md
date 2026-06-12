---
title: "Vista fails to load after dual boot"
date: 2012-08-07
forum: Installation &amp; Upgrades
---

### Post by dwaldon on 2012-08-07
Hi all,

I recently installed ubuntu to dual boot alongside windows vista, and I'm hitting a bit of a snag trying to get windows to boot now. The laptop I'm running on has both a main drive and a second 'recovery' drive, and both show up on the GRUB boot menu (as sda1 and sda2). However, when I select the main drive (sda1, correct?), I get to the 'windows is loading' screen with the black background, the windows flag, and the loading bar, and then my laptop reboots. I've tried starting windows in safe mode (with and without command line) and nothing seems to be working... any ideas, short of a full system wipe?

---

### Post by oldfred on 2012-08-07
Often chkdsk is the first thing to try, see this link :)

[http://ubuntuforums.org/showthread.php?t=1913477](http://ubuntuforums.org/showthread.php?t=1913477)

If chkdsk does not work, then other Windows repairs may be necessary, but if getting a boot screen that is a start. Some Windows installs do have recover as first partition and install second, so it just depends on your configuration.

---

### Post by Mark Phelps on 2012-08-08
If you don't have a Vista Recovery CD, then you will need to go to the link below, pay the price, download and burn the image to a CD -- and boot from that:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

You will most likely have to run the repair three times -- Vista only repairs one thing at a time and generally takes three passes to do all the repairs.

---

### Post by oldfred on 2012-08-08
If you know anyone else with the same 32bit or 64bit version of Windows you make make your own repairCD.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I also have used a Windows 7 repair USB (64bit) to run chkdsk on an XP (32bit) install, so some tasks can be run from a different version, but best to have same version if you need to run major repairs.

---

