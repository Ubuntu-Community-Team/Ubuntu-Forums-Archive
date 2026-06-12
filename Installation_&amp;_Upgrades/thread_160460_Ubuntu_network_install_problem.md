---
title: "Ubuntu network install problem"
date: 2006-04-15
forum: Installation &amp; Upgrades
---

### Post by JBull on 2006-04-15
I'm doing a network install of Breezy.  I have to pass the option acpi=off option to the installer kernel or it won't detect the network card.  So I turn off acpi and start the install.  Card detected.  DHCP works.  Install begins.  Downloads for about 10 minutes and then installs GRUB.  Then it wants to restart and continue install.  Upon restart the installer tries to go to the Ubuntu mirror but can't connect.  I know why:  in the new /boot/grub/menu.lst  the option is not set for acpi=off.  Therefore it can;t start the network card.  I can get to the command line and put acpi=off.  But the installer is done.  Now when I boot I get the command line and login.  But there is no resume of the second phase of installation.  I have no X window.  startx gets "command not found".

How do I resume the install?  Or start installer from the beginning and tell it to keep the acpi=off so that network card works?  I have no way of telling what kernel options I want when the installer sets up teh new GRUB.  Very annoying problem.  If I don;t solve this I'll have to go back to FC4.

BTW, I dont have a working CD drive or floppy on this laptop (Thinkpad T20).

---

### Post by JBull on 2006-04-15
Ok, I couldn't find an answer anywhere so I figured it out on my own.

When the installer wants to reboot , select the option "Go Back". You are given a list of things to do. One of the last options is "execute a shell" Select this option. Then a message appears that the image is on ramdisk and tells you how to mount it. Mount it and go to boot/grub/menu.lst

vi is not available to edit. You have to use "nano" to edit the file. Insert kernel options. The option I added was acpi=off apm=on.  Save the new menu.lst  Exit the shell by typing "exit". Then allow the installer to reboot.

Upon reboot the installer enters phase 2. The NIC is now detected and finds an IP adress! Installation resumes and completes successfully!!! Hello Ubunto Breezy!

---

