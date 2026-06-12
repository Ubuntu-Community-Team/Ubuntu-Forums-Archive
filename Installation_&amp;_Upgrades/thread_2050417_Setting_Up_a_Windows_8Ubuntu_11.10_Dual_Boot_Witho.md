---
title: "Setting Up a Windows 8/Ubuntu 11.10 Dual Boot Without Wubi?"
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by Moose on 2012-08-30
Hey guys.
I have Windows 8 currently running on my HpG62 Notebook. I had ubuntu 11.10 running via wubi install. I uninstalled that and i want to do a full install. I have a 500GB internal hardrive. I want windows to take up 200GB and Ubuntu 100GB and i want to have a 200GB storage partition. I know how to do all of this. But what confuses me is this: Do i need a swap partition. And also, do i need to install an additional bootloader to get a boot menu? Or does Ubuntu do that automatically when i install. SO Basically what i am doing is shrinking my windows partition t0 200gb and Using 100 for ubuntu. Will it be as easy as installing Ubuntu to the 100gb unallocated space? And a boot loader automatically is installed?
If you guys help that would be much appreciated.

---

### Post by Moose on 2012-08-30
Bump, can you please answer?

---

### Post by oldfred on 2012-08-31
Use Windows to shrink the Windows partition, but not to create any partitions.

And Ubuntu will install to the unallocated space with just / (root) and swap partitions. This assumes you have not already used all 4 primary partitions. If you want more than / & swap like a separate /home, then you have to use Something else or manual partitioning and create, choose format and what partition is mounted as (/, /home etc).

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

You should have repairCD/USB or liveCD for every system you have installed.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

Grub will be with the auto install, automatically installed to the MBR of sda. It should add the Windows boot entry, but if Windows is in the hibernation mode you may have trouble. Someone posted you can turn that off.

---

