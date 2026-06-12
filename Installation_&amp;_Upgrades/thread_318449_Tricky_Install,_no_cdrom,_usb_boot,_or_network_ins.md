---
title: "Tricky Install, no cdrom, usb boot, or network install"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by avalonpimp on 2006-12-14
I have an old dell laptop 3800, running Edgy. Awesome Distro. But i want to use the Svideo out to watch videos on my TV, and i just cannot get the drivers to work. So i have to go back to XP! But....the cdrom is broke! 

Cant USB boot, or network install. Floppy works
Drive is formatted as ext2

i think my solution might lie here.... [http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

this focuses on going from XP, to Linux. I need to go to Linux to XP.

I can use network to transfer files( i.e. XP install), so how can i get the XP installation program to boot using GRUB? 

Reference #2 [http://www.linuxforums.org/forum/installation/47887-install-linux-laptop-no-cd-rom-floppy.html](http://www.linuxforums.org/forum/installation/47887-install-linux-laptop-no-cd-rom-floppy.html)
 - notice how he  copied sys files to make it boot, and i386 folder

---

### Post by Cderugg on 2006-12-14
You'll have to edit your grub list. $ sudo gedit /boot/grub/menu.lst   Than at the bottom add your OS for example... 

title		XP Media Center
root		(hd0,0)
savedefault
makeactive
chainloader	+1

note that My XP is on the first (only) hard drive and first partition (hd0,0)

I didn't read to much of your article link, but I think if you make a fat32 partition, copy the I386 folder to it, make a dos boot floppy and run winnt.exe in the I386 you might be able to install XP that way.  You could convert to ntfs later or do it from the start and get the ntfs4dos boot floppy from avira. Good luck

---

