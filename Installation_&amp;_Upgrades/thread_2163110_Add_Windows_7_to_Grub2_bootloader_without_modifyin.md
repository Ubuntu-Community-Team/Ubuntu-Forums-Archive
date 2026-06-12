---
title: "Add Windows 7 to Grub2 bootloader without modifying windows bootloader"
date: 2013-07-17
forum: Installation &amp; Upgrades
---

### Post by RedLionRisen on 2013-07-17
Hello.  I have a two hard drive system that I've had difficulty setting up with Ubuntu 12.04 and Win7.  I had originally installed Ubuntu on my larger 1TB hard drive through a USB connection, then switched it to the first Sata port on my system, and now have the main hard drive in the 2nd Sata port.  As such, the hard drive with the Ubuntu install is designated sda, and the one with Win7 is now sdb (with the windows boot files on sdb1).  So far I've succeeded in getting both systems to boot up on completely separate bootloaders, with no errors.  With the Win7 hard drive in Sata1, and the Ubuntu drive in USB, if I used the automaic boot repair option in Ubuntu, it would go the extra mile of combining the boot options (and modifying the Windows boot partition in the process), which was what I wanted since I could boot either Ubuntu or Windows from one menu.  However, doing that innevitably gave me erros with resuming Windows from hibernation, which I can't work with,  After much experimenting, it seems any modification of the Windows boot partition will result in such errors.  I need to be able to boot Win7 from grub without modifying its boot partition at all.  Again, the current (and hopefully permanent) setup is the Win7 SSD on the 2nd Sata port with the boot partition as sdb1, and Ubuntu on the first Sata port HDD.  Thank you for your help!

---

### Post by Mark Phelps on 2013-07-17
I do this all the time -- as I don't like messing around with the Windows boot loader ...

Do the following:
1) Set your machine to boot from the Ubuntu drive by default
2) Once booted into Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the GRUB config files and add an entry for the Windows 7 Loader.
3) When you then reboot, you should be presented with a GRUB menu with entries for Ubuntu and for Windows.

---

### Post by oldfred on 2013-07-17
Hibernation can always create issues. If booting with a SSD hibernation should not be saving all that much time.

this standard list of links is for Windows 8 as it always uses hibernation of one sort or the other.
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)

---

