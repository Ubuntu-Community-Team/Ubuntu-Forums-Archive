---
title: "Upgading Windows 7 with a dual boot system with Ubuntu 12"
date: 2014-05-10
forum: Installation &amp; Upgrades
---

### Post by kwjorders on 2014-05-10
Hey I need to upgrade my Window7 PC to Windows 8 which currently has Ubuntu 12 (I think) dual booted with grub and was wondering if my linux system would tolerate my new windows 8 setup and if there is any problems I might run into doing this.  My setup is a little different then most dual booted systems in that the Ubuntu is loaded on its own hard drive instead of partitioning.  I hope that is enough info.
-Thanks and any help would be greatly appreciated.
Kylor W. Jones

---

### Post by grahammechanical on 2014-05-10
If you install Windows 8 on to any of those hard drives the installer will put the Windows bootloader on to both hard drives and you will not be able to boot Ubuntu no matter what hard drive you select through the BIOS/UEFI system. That is what happened to me. Two possible ways to prevent this.

1) Disconnect the drive with Ubuntu on. Let us say it is sdb. Then after Windows 8 is installed reconnect the drive and use the BIOS/UEFI to boot into sdb/ubuntu and then open a terminal and run

```
sudo update-grub
sudo grub-install /dev/sdb
```

Then the Ubuntu bootloader will be updated to notice the presence of Windows 8 and the updated bootloader will be installed into sdb. So, when you boot into sdb you will get a grub menu from which you can load either Ubuntu or Windows 8. Or you can use the BIOS/UEFI system to select the drive with Windows on and there will be no option to load Ubuntu.

2) Let the Window installer do its worse. Then run a Ubuntu live session and use File Manager to open drive/disk sdb. That will mount the drive. Then open a terminal and run

```
sudo update-grub
sudo grub-install /dev/sdb
```

That is what I did to fix this rude behaviour. Once you can boot into Ubuntu again you may need to run those two commands to put the Windows 8 install into the Grub/Ubuntu boot menu.

Now, I do not want anyone to get the wrong idea. I only installed a Windows 8 pre-view session and it was only done as an experiment. :)

Regards.

---

### Post by oldfred on 2014-05-11
Windows default install also creates a 100MB boot partition. And it puts that partition on the drive set as boot in BIOS. So be sure to change BIOS to boot Windows drive if you do not disconnect Ubuntu drive. Otherwise it just may force a 100MB NTFS partition into the Ubuntu drive and corrupt partition table as it does not correctly see Linux partitions.

You also need to turn off fast boot or the always on hibernation.

 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

