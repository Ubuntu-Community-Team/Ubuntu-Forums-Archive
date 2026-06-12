---
title: "Uncompleted installation."
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by a20070704 on 2007-11-01
Hello All!

I installed Ubuntu 7.04 (feisty) on a separate  drive (the other has XP ( argh...)  on it ) and been using it a while.
My Pc motherboard crashed and was replaced by a new one of the same kind.
Since then no installation, 7.04 or 7.10,  completes as it should. 
The live CD manages to launch and when I start installing, I don't get the "Installation Complete" message. The installation completes  immediately after "creating user" and I get /target/home
and /target mounted on the desktop (of the live CD).

When I boot the machine I get a grub error 15.

I assume something in the PC configuration is getting in the way.

The alternate cd started giving me jibrish durint the installation.

Is there any log of the installation that will help me find what the problem is?

If the problem is known please tell me how to solve it.

Al

---

### Post by esagherardo on 2007-11-01
Sorry; I mismatched the threads. This is not an answer to that question.


-------

The problem seems to be the numbering of devices under grub on live-cd. Actually a bug of the live-install.

When live-cd is running, (hd0) may not be the HD. You must devise the number given to the HD, say e.g. (hd1); the actual number depends on your machine.

When installing, select "advanced" from the partitioner, and replace (hd0) with (hd1).

This allows to correctly install grub, up to one possible configuration error in the menu.lst. If the freshly installed system does not boot, you got this error, and you have to correct it.

The problem is that grub might number differently the devices when using the installed system instead of the live-cd. Let's say that, after reboot, your HD is (hd0); then /boot/grub/menu.lst  contains the wrong "root" entry, set to (hd1,1), which was used during the grub-install, and which should be (hd0,1).

To cope with, boot the live-cd, mount the physical device where /boot of the installed system is (not the /boot of the live virtual filesystem), cd into it, edit grub/menu.lst, change (hd1,1) into (hd0,1).

Warning: (hd0)(hd1)(hd0,1)(hd1,1) used here may be different on your system. 

Hope it helps.

Gherardo

---

