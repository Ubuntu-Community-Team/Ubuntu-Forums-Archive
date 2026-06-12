---
title: "Windows 7 + Ubuntu dual boot -- Windows won't load"
date: 2014-10-22
forum: Installation &amp; Upgrades
---

### Post by SeishiroSakura on 2014-10-22
I recently bought a laptop (lenovo g50-70 in case it matters) with freedos (which I got rid of).

I then proceded to install Windows 7 64bit on a 150gb partition and went on to install Ubuntu 14.04.1 LTS 64bit on another 150gb (and another for swap). The rest of the disk I left unallocated and is meant for storage purposes later on.

Both OSs installed problem free but after the Ubuntu installation, when attempting to load W7 all I get is some distorted graphics and a frozen screen.

I tried out Boot Repair ([http://paste.ubuntu.com/8628378/](http://paste.ubuntu.com/8628378/)) to no avail.

Any thoughts?

---

### Post by oldfred on 2014-10-22
Install looks normal.
Boot-Repair can only do very minor Windows fixes.

Grub really only boots working Windows. Did Windows boot ok before installing Ubuntu?
Did you shrink Windows using Windows own partition tools and immediately reboot so it can run chkdsk?

You may be able to reinstall a Windows boot loader temporarily using Boot-Repair and use f8 to get into Windows repair console. The sda1 boot partition boot only. Using f8  from grub menu is real difficult as it is so quick, but a few said it does work if you are quick enough and try several times. Or use a Windows repairCD or flash drive.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

