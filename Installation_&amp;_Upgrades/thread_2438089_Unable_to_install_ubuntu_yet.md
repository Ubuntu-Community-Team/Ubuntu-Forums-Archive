---
title: "Unable to install ubuntu yet"
date: 2020-03-05
forum: Installation &amp; Upgrades
---

### Post by WhiteTigerIT on 2020-03-05
I have two PCs.
Win10 Home and Xubuntu were installed on the first.
Win10 Pro and Kubuntu were installed on the second.
On both PCs there was nothing important about Linux partitions.
Win10 has been installed on both PCs **again**, but now I can no longer install the two **xubuntu** (19.10 nor 18.10) because it gives me writing error on the disk.
I have tried the installation in various ways and the problem is the same on both PCs.
My idea is that there is a trace of previous installations in the UEFI partition which now no longer allows me to install new ones.
Thanks in advance for help and any advice.

---

### Post by CelticWarrior on 2020-03-05
1. 18.10 is EoL, out of support, shouldn't be used.

2. > My idea is that there is a trace of previous installations in the UEFI  partition which now no longer allows me to install new ones.

This is incorrect. And you wouldn't need to reinstall any just because you reinstalled Windows, especially in a UEFI system where bootloaders co-exist peacefully.
In Windows, always disable Fast Startup before attempting to dual-boot. That's the likely cause for the vague "gives me writing error on the disk" (when posting please include the complete error messages).

---

### Post by WhiteTigerIT on 2020-03-07
> **CelticWarrior said:**
> 1. 18.10 is EoL, out of support, shouldn't be used.

2. 

This is incorrect. And you wouldn't need to reinstall any just because you reinstalled Windows, especially in a UEFI system where bootloaders co-exist peacefully.
In Windows, always disable Fast Startup before attempting to dual-boot. That's the likely cause for the vague "gives me writing error on the disk" (when posting please include the complete error messages).

In Windows 10 Pro and in the BIOS the options are set correctly.

The error is:
[INDENT]An error was encountered in copying the files to the hard disk.[/INDENT]
[INDENT][Errno 5] Input / Output error
[/INDENT]

This is the screenshot
[https://i.imgur.com/dzCDGzZ.jpg](https://i.imgur.com/dzCDGzZ.jpg)

---

### Post by yancek on 2020-03-07
This is an English language forum so that if you want to post here, translate the error into English and re-post.

---

### Post by oldfred on 2020-03-07
Windows may have reset UEFI settings.
Double check that fast boot is off, drive is set for AHCI and perhaps some other UEFI settings based on what brand/model system?
I have to reset 7 or 8 settings every time I update UEFI. You should also check you have latest UEFI, but Windows may have done that and that is why you need to update settings.

Also Windows defaults to fast start up/hibernation. That must be off for Ubuntu installer to be able to see the NTFS partitions.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

