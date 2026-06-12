---
title: "boot repair error"
date: 2013-07-16
forum: Installation &amp; Upgrades
---

### Post by navvirdi15 on 2013-07-16
[http://paste.ubuntu.com/5881463/](http://paste.ubuntu.com/5881463/)

---

### Post by oldfred on 2013-07-16
You do not have a very large / (root) partition at 8GB, but that should be enough to boot. I have a full install in 8GB on my 16GB flash drive for emergency boot, but do not install lots of apps.

You are showing several errors. Did you turn off secure boot and does Windows still boot if secure boot is off? Have you turned off fast boot as then Windows is in hibernation and causes issues and sometimes major issues.

You are also showing the locked efi partition. That cannot happen, but it somehow does. Some have fixed it just by mounting it in Windows and running chkdsk. Others have to fully back it up, delete the entire partition. Then create a new FAT32 partition with the boot flag from gparted and restore all the efi files & folders.
       grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)

Please review link in my signature as installs to UEFI systems with Windows 8 are not yet straightforward. 

      
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

