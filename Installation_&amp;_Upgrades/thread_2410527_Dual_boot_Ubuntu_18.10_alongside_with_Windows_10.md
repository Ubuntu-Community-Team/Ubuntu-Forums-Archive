---
title: "Dual boot Ubuntu 18.10 alongside with Windows 10"
date: 2019-01-16
forum: Installation &amp; Upgrades
---

### Post by kamil172 on 2019-01-16
Hello,

I try to install Ubuntu 18.10 alongside with Windows 10. but I have a problem with that installation.


[ATTACH=CONFIG]282217[/ATTACH]

---

### Post by oldfred on 2019-01-16
It looks like your Windows may be BIOS with MBR partitioning.
So then you want to boot Ubuntu installer in BIOS boot mode, so it installs in BIOS mode.
Windows only boots in UEFI boot mode from gpt and then you would already have an ESP - efi system partition.

Make sure Windows fast start up is off. Windows updates will turn it back on and then grub will not boot Windows.
And make Windows repair flash drive, so if Windows updates does turn fast start up back on and you do not see it, and then grub does not boot Windows, you have a way to repair & boot Windows. Keep Ubuntu live installer so you can restore grub after fixing Windows.

Since you booted installer in UEFI mode, it must be a newer system, or within last 5 years.
But you must have installed Windows in the now 35 year old BIOS/MBR configuration.
UEFI has CSM for backwards compatibility.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

