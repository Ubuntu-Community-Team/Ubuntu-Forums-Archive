---
title: "Dual Boot / Grub2 / existing Windows 7 and fresh ubuntu 13.04"
date: 2013-07-12
forum: Installation &amp; Upgrades
---

### Post by regis.dev on 2013-07-12
Here the situation : i try to do hava a dual boot on separate two hard drives (primary disk UBUNTU, second disk WINDOWS 7) 

I got two hard drive : 
(SATA)sda => ubuntu 12.04
sdb => windows 7
here the (boot info) [http://paste.ubuntu.com/5851196](http://paste.ubuntu.com/5851196)
In this situation everything was going well : i could choose in grub menu wich os to boot.

==

I bought a new ssd hard drive, i unplug my first drive (sda) from the motherboard, i plug my new hard drive as a primary disk (the motherboard boot by default on it)
I install a fresh ubuntu 13.04 on a new hard drive (which is the primary disk in the bios), i can boot on it everything is working well.
During the installation it didnt detect windows 7 on the other drive.
Grub doesnt detect at all my second hard drive with windows 7, i can t boot on it.

here my current boot info => [http://paste.ubuntu.com/5868177](http://paste.ubuntu.com/5868177)

I try to reinstall the grub, to run boot repair, also os-proper,  nothing works, .
I dont know what to do ??? i search on web / forum but i found nothing which can help me

Thanks

NB: if I plug my old hard drive with old ubuntu i can boot on windows

---

### Post by regis.dev on 2013-07-12
I think i now what i have to do : restore the windows Bootmgr (recreate the 100mb first partition in primary disk (sda) used by windows)

But how i can recreate this partition in my sda drive, this is what i want to do


sda1: _________________________________________________________________________ 
     File system:       ntfs     
Boot sector type:  Windows 7/2008: NTFS 
    Boot sector info:  No errors found in the Boot Parameter Block.     
Operating System:       Boot files:        /bootmgr /Boot/BCD

Any ideas ?

---

### Post by oldfred on 2013-07-12
When you installed Windows to sdb, you still had sda as the boot drive in BIOS. Windows installs its boot files to a primary NTFS partition with the boot flag on the drive BIOS boots from which usually works. 
Grub just installs to sda which also usually works. But may not be boot drive in BIOS.

Windows 7 will boot from one partition or just your sdb1. The main reason for the separate Boot partition was so you could encrypt your main install. But the Boot partition also has the Windows recovery (or repair) tools. But better to have a Windows repairCD or flash anyway with the repair tools.

Just copy Windows boot files into your Windows install. Boot repair usually copies bootmgr as a backup also.
Files & folder you need to boot, copy to root or top level of Windows in sdb1. I would also install a Windows boot loader to the MBR of sdb, so that drive would boot without any other drives.
 /bootmgr /Boot/BCD

If you boot Windows you can make this and also use it to repair your Windows using the Windows procedures.

 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

      
 How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

---

