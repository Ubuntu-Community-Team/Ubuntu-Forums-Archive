---
title: "Tried to Install Ubuntu 9.10 on a USB drive"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by jcdavies on 2010-04-08
Last night i tried to install Ubuntu on a 8gb usb drive had no problems with the installation but not the computer wont boot at all. when the usb is plugged in it just gets to the page saying grub and the little white line just keeps flashing it gets no further. If the usb drive isn't plugged in it says something about grub can start i will get this error msg tonight, 

can any one help me though it would be greatly appreciated even just to get me back in to windows.

thanks for your help

---

### Post by ghostborg on 2010-04-08
If for some reason you find the need to get back to your Windows XP bootloader instead of the one installed by your Linux distro, simply follow these instructions:

1. Boot up with your Windows XP disc.

2. Select the option Recovery Console.

3. At the prompt, type "fdisk /mbr" (without the quotes of course)

4. Restart your computer.


To FIX VISTA MBR: Boot up from Vista Installation DVD and select Repair Your Computer option (its below Install Icon). Select Windows Vista -- Command Prompt.
Execute this at command prompt:
Code:
bootrec.exe /fixmbr
bootrec.exe /fixboot

Should work for Win7


Got this info from other forums

---

### Post by oldfred on 2010-04-08
Often grub installs to the internal drive unless you specify otherwise. At the end of the partitioning screen during install is an advanced button that lets you choose where to install grub.

ghostborg's way will get you back to windows.

If you need to install grub to the USB:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by jcdavies on 2010-04-08
> **ghostborg said:**
> If for some reason you find the need to get back to your Windows XP bootloader instead of the one installed by your Linux distro, simply follow these instructions:

1. Boot up with your Windows XP disc.

2. Select the option Recovery Console.

3. At the prompt, type "fdisk /mbr" (without the quotes of course)

4. Restart your computer.


To FIX VISTA MBR: Boot up from Vista Installation DVD and select Repair Your Computer option (its below Install Icon). Select Windows Vista -- Command Prompt.
Execute this at command prompt:
Code:
bootrec.exe /fixmbr
bootrec.exe /fixboot

Should work for Win7


Got this info from other forums

will it work for windows 7 as well?

---

### Post by jcdavies on 2010-04-08
sorry just reread your post thanks for your help greatly appreciated

---

### Post by jcdavies on 2010-04-09
this worked great thank u

---

