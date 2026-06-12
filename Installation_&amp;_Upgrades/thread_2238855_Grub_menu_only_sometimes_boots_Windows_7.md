---
title: "Grub menu only sometimes boots Windows 7"
date: 2014-08-10
forum: Installation &amp; Upgrades
---

### Post by gmen6981 on 2014-08-10
I have a similar problem, but with Windows 7. After installing Ubuntu 14.04, when I restart the computer, if I choose Windows from Grub menu I will see the "Starting Windows" screen, then the computer will restart. every so often ( 1 in 5 tries?) windows will actually start. Ran Boot repair in Ubuntu, and tried Easy BCD in windows, both with no help. Any suggestions are greatly appreciated!

---

### Post by oldfred on 2014-08-10
Moved to your own thread since the thread you posted in is related to Windows 8 and issues specific to UEFI boot with Windows 8.
Are you booting in UEFI or BIOS boot mode.

Grub really only boots working Windows, but that sometimes it works is very strange.

Just to confirm configuration, run the Boot-Report report, but do not run any auto fix. Boot-Repair really only fixes grub boot issues and only can fix a few minor issues. Most need a Windows repairCD or flash drive. If you can get into Windows make a repair CD or flash drive, as otherwise it costs to buy one.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

---

