---
title: "Windows XP does not start using GRUB"
date: 2005-06-07
forum: Installation &amp; Upgrades
---

### Post by Tjeerd_Boersma on 2005-06-07
I installed Hoary on a computer which also runs Windows XP professional, so the installation program made a GRUB-file which should make booting possible in Windows as well as in Ubuntu. However, after installation Windows does not start anymore. Does anybody know this problem? Of course I can start the computer with the Windows Installation Cd and run a 'fixmbr' in the recovery mode, but then ubuntu will not work anymore. Maybe it's possiple to make some changes in GRUB but I would not know how. I hope someone has an idea of how to solve this problem.

Greetings, Tjeerd Boersma

---

### Post by zwaardmeester on 2005-06-07
Hi,

I think you need a bootloader of some kind for this, for example Grub for linux or BootMagic for Windows. You don't need both of course, I only mention the platform from which you can configure them. How make a dual-boot system with grub you can read [here](http://www.ubuntuguide.org/#restoregrubmenuafterwindowsinstallation). However, this will only work when windows is on the first partition of the first harddrive (hd0). If it is not, you need to map the windows partition to (hd0) and vice versa. How to do this is discussed [here](http://www.ubuntuforums.org/showthread.php?t=38050&highlight=grub+map) 

veel succes!

---

### Post by zAo on 2005-06-07
What error do you get when you want to start Windows?
Grubs config file is here:

/boot/grub/menu.list

Check the deveice it points to (hd 0,0 for example)

---

### Post by Gary Powers on 2005-06-07
[QUOTE=Tjeerd_Boersma]I installed Hoary on a computer which also runs Windows XP professional, so the installation program made a GRUB-file which should make booting possible in Windows as well as in Ubuntu. However, after installation Windows does not start anymore. Does anybody know this problem? Of course I can start the computer with the Windows Installation Cd and run a 'fixmbr' in the recovery mode, but then ubuntu will not work anymore. Maybe it's possiple to make some changes in GRUB but I would not know how. I hope someone has an idea of how to solve this problem.

Greetings, Tjeerd Boersma[/QUOTE]

Tjeerd, make sure that your hard drive (in BIOS settings) is set to LBA, not AUTO.

Gary

---

