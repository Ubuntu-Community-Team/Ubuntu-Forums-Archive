---
title: "ATi Video Driver"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by jgcamp99 on 2006-11-21
If it hasn't already been done, I'd like to see this added to the wiki for the fglrx for the ATi video driver update that can be performed manually. 

It has happened on 8.29.6, 8.30.3 and now, 8.31.5 with Edgy. This file located here in the filesystem:

/etc/x11/xorg.conf

you'll notice this code section:

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	**Option	    "OpenGLOverlay" "on"**
EndSection

Every time I've performed an ATi driver upgrade, the OpenGLOverlay setting has been turned to "off" in this section. And everytime I've gone to reboot after the upgrade, Ubuntu Edgy has crashed or locked up. The only way I could fix this problem was to go in under grub's recovery mode (multiboot system), enter the root password that I re-enabled (thank God for that), "gdm as root" at the prompt command gets me to the login screen, then change the session to gnome failsafe mode and log in as root. Even there, it's not a guarantee that you won't be kicked out several times before you get an opportunity to fix this issue. But the solution to this problem is to go into the xorg.conf file using gedit (text editor) and changing the word "off" to "on" prior to the reboot. Make sure you save the file, before rebooting. If you aren't experienceing this issue, it wouldn't hurt to check it before upgrading to see what it is, then rechecking it after the upgrade, prior to reboot.

---

