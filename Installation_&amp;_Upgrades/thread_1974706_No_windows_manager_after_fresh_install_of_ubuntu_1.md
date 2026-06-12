---
title: "No windows manager after fresh install of ubuntu 12.04"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by cactux on 2012-05-06
Hello,

On a PC running Ubuntu 9.04 fine, I installed Ubuntu 12.04.
I just have the screen background: no menu is displayed. I can not even start an app with ALT+F2.
I can not start any app. The system is useless.
If I switch to console mode (ALT+F1) I can restart the system with sudo reboot.

What can I do?

The live CD works fine, I don't understand why it does not work once installed. The previous version 9.04 was working fine.

Thanks for your help ;-)

---

### Post by oldfred on 2012-05-06
Many are having issues with video drivers. What video card do you have. I have nVidia and have to use nodmodeset on first boot until nVidia driver is installed.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

If you can get to command line, you can use it to install nVidia or ATI drivers, not sure about others.

---

### Post by sanderD on 2012-05-11
did you find a solution? I have the same problem. A new install of ubuntu 12.04, the live cd work perfectly for me. But unity 3d does not work (2d works). Ive tried to install ati drivers (fglrx) but nothing seems to work.

---

