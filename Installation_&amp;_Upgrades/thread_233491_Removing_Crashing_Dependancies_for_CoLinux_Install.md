---
title: "Removing Crashing Dependancies for CoLinux Install"
date: 2006-08-10
forum: Installation &amp; Upgrades
---

### Post by FR47 on 2006-08-10
Greetings.

After about two weeks of work I got CoLinux to boot up with Ubuntu 6.06 in text mode, and in X mode through a VNC.  However, I'm having trouble with installing the Ubuntu desktop packages for Gnome.  My specific problem lies in that parts of Gnome and the desktop require certain packages, most notably ACPI support, to be installed.  This is not something CoLinux likes at all, as it promptly crashes without so much as an error message.  It also seems to do similarly for anything involving VESA and laptop-specific programs as well.  For those who are unfamiliar with CoLinux, these programs are NOT useful in any way; all graphical services are provided through external X servers or VNC connections, and power management-type services are basically useless for it.

Exacerbating this is the fact that most of the time the installation of the package is half-done due to the program crashing when being started up during installation, leaving a mess for dpkg to try to clean up, usually resulting in more crashes.  I've tried manually (repeatedly) cleaning out /etc/rcX.d, but this will only get me so far.

My question is, what would you recommend I do to keep using CoLinux and avoid these unwanted dependancies and still have Gnome and an otherwise upgradable system without worrying that dpkg/apt/Synaptic/etc. will accidentally start this whole trouble again if I try to upgrade the wrong package?  This is particularly vexing as at the moment the system is stuck on the obviously-important gnome-panel package.

Thank you for any help you can give me.  This is extremely frustrating.

---

### Post by motscousus on 2006-10-27
install ACPI and prevent it from starting at boot time.


[http://ubuntuforums.org/showthread.php?t=81444](http://ubuntuforums.org/showthread.php?t=81444)

---

