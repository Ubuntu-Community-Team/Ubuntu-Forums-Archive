---
title: "Installing 11.10 via Intel AMT/KVM - Blank Screen"
date: 2011-12-20
forum: Installation &amp; Upgrades
---

### Post by globichen on 2011-12-20
Hi,
 
did anyone manage to install Ubuntu 11.10 (Desktop or Server, 64 Bit) using Intel's built in AMT KVM on Sandy Bridge?
 
I manage to mount the ISO and I see the install menu, where I can choose various options (langage, keymap, etc...). After I run "Install Server", I just get a blank screen on my VNC, basically forcing me to reboot eventually and start over again with the same result each time.
 
Various options in F6 install prompt, especially nomodeset did not change anything.
 
Suprisingly this only happens with Ubuntu ISOs. Debian, Windows 2008 and even ESXi 5 ISO went well all the way.
 
Could this be GPU driver related?
 
CPU: i7-2600 with AMT 7
 
 
Thank you.
 
Andy

---

### Post by globichen on 2011-12-20
Also interesting:
 
I just tried installing 10.04 via AMT/KVM from ISO. This went smooth all the way!
 
So why would I get a blank screen on a 11.10 ?
 
 
Andy

---

### Post by MAFoElffen on 2011-12-20
> **globichen said:**
> Also interesting:
 
I just tried installing 10.04 via AMT/KVM from ISO. This went smooth all the way!
 
So why would I get a blank screen on a 11.10 ?
 
 
Andy
Each version since 9.04 made graphics changes in grub, kernel and xorg. Not just with Ubuntu, but with Linux itself. Ubuntu Server made changes to the VGA graphics in the console, that also takes advantage of these graphical enhancements since version 11.04.

There are now additional post-installation adjustments for these.  For reference, please read the first 3 posts of:
**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

---

