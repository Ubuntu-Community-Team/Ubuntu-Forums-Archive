---
title: "Help!"
date: 2015-11-11
forum: Installation &amp; Upgrades
---

### Post by John_Pawlikowski on 2015-11-11
After I tried to uninstall my dual-booted Ubuntu partition on Windows, I accidentally deleted the wrong one. Now, I have a GRUB loader with a black screen. I have my old Ubuntu USB which I used in the first place, but I don't have a Windows DVD. What do I do? Help!

Thank you in advance,
John.

---

### Post by oldfred on 2015-11-11
If you did not otherwise damage Windows you can use Boot-Repair or command line to install a Windows like boot loader to the MBR.

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

But most fixes for Windows require a Windows repair CD or flash drive.
      
 Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by John_Pawlikowski on 2015-11-11
Holy crap, I somehow fixed by typing "exit" in the grub terminal. I now may run windows!
I still want to uninstall and reinstall ubuntu though.

---

### Post by sammiev on 2015-11-11
If you want to reinstall Ubuntu, just install over top.

You should see that option when you go to install Ubuntu.

---

