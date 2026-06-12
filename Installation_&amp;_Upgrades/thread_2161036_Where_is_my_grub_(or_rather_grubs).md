---
title: "Where is my grub? (or rather grubs)"
date: 2013-07-09
forum: Installation &amp; Upgrades
---

### Post by Zardoz777 on 2013-07-09
I have a dual boot system (Windows 7 + Ubuntu)

In my sda hard drive I have installed Windows.
In my sdb Solid State drive I have Ubuntu.

If I set in the bios to boot from sdb the computer does not boot. It can only boot if I set the bios to boot from sda.
But using the bootinfoscript it looks like grub is in my sdb drive, which is a contradiction:  

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe
sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

But in another line of the output of the same screen, it says that grub is installed in both drives..which makes me crazy!

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 72 for .


Anybody understands what is going on? I would like to boot from sdb only.

---

### Post by dino99 on 2013-07-09
sudo dpkg-reconfigure grub-pc

---

### Post by Zardoz777 on 2013-07-09
Can you tell me what will do that command?

---

### Post by oldfred on 2013-07-09
You can use Boot-Repair or your Windows repairCD to install a Windows boot loader to sda. I think Dino's command will just let you reinstall grub to sdb, which you may want to do, to make sure you have the most current version in sdb and that grub remembers to reinstall grub to sdb not sda on major updates.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

If you do not have a Windows repairCD make one. You must have a repairCD or LiveCD for the current version of every system you have installed.
      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

