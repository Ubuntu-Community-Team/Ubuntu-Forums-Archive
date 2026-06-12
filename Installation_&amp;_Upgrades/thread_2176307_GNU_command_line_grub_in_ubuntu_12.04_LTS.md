---
title: "GNU command line grub in ubuntu 12.04 LTS"
date: 2013-09-23
forum: Installation &amp; Upgrades
---

### Post by karthik1124 on 2013-09-23
Hi all, 

I have a 1 TB HP Hdd with a preinstalled windows 8 OS. I installed ubuntu 12.04 LTS and during the installation, i encountered an error that the grub2 had failed to install. So i did a boot repair and now, i am stuck with a command line GNU grub. I am not able to log in to windows and  i am working on ubuntu live using the USB. Here is a copy of the file i received on using the boot repair tool. I can see that there are some errors but i am unsure as to how to rectify them without deleting data from windows.

[http://paste.ubuntu.com/6147312/](http://paste.ubuntu.com/6147312/) 

Thanks

---

### Post by oldfred on 2013-09-27
The main error I see is that grub menu has no boot entries. Grub2's os-prober normally creates entries for Ubuntu and Windows. The Windows entries from prober are wrong but then Boot_Repair creates correct entries in 25_custom and it could not create that file. More like grub was not ever installed?

It also looks like you tried to install wubi, which does not work with gpt partitioned drives (all UEFI systems). You can just uninstall it or delete it from Windows.

It may be easiest to just try a new install? If you try that either use gparted on live installer to delete Ubuntu partition or use Something Else or manual install to choose existing sda6 as /.
But I prefer to have smaller system / (root) partition of 25GB and separate /home. With Windows you may want to have a shared read/write NTFS data partition. Windows 8 in particular should not be written into from any other system even anther Windows install, but can be set as read only when mounted in Ubuntu.
Also make sure fast boot is off in Windows 8.

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
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)
User who fixed Windows 8
[http://ubuntuforums.org/showthread.php?t=2171156s](http://ubuntuforums.org/showthread.php?t=2171156s)

---

