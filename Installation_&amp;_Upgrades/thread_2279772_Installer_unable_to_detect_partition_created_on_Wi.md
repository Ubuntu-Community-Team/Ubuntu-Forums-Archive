---
title: "Installer unable to detect partition created on Windows 8.1 Pro"
date: 2015-05-26
forum: Installation &amp; Upgrades
---

### Post by AngryMuffin on 2015-05-26
On my machine there is an SSD containing my Windows 8 as well as the 16 GB unallocated partition, and an HDD for all my other data. When I boot into the XUbuntu installer it isn't able to detect the partition on the SSD and I have no idea why. I'm trying to create a dual boot, and use the windows 8 boot manager if possible.

---

### Post by Vladlenin5000 on 2015-05-26
Hi and welcome.

You need to disable fastboot in Windows and make you're shutting down, not rebooting. Otherwise, the new Windows default is to have the partitions it manages hibernated. The installer cannot recognize those partitions if they're hibernated.

You can't use Windows 8 boot manager for anything but other Windows versions. Plus, if your system is UEFI - it certainly is if the Windows 8 was factory installed - then you should read and understand this, before anything else: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by AngryMuffin on 2015-05-26
> **Vladlenin5000 said:**
> Hi and welcome.

You need to disable fastboot in Windows and make you're shutting down, not rebooting. Otherwise, the new Windows default is to have the partitions it manages hibernated. The installer cannot recognize those partitions if they're hibernated.

You can't use Windows 8 boot manager for anything but other Windows versions. Plus, if your system is UEFI - it certainly is if the Windows 8 was factory installed - then you should read and understand this, before anything else: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I've disabled fastboot and I've also shut down as opposed to rebooting, and it still does not detect the drive. I'm hesitant to just simply install via Trial and Error because I've mucked up my operating system before by doing so. Is there a difference in the way partitions work in SSDs and in HDDs? I'm trying to partition my SSD and most of the tutorials I see are on HDDs. Thanks in advance!

---

### Post by Geoffrey_Arndt on 2015-05-27
One alternative worth trying (IMHO) is to run "gparted" (via live cd/dvd/flash-stick) and format the unallocated to ext4 . . . perhaps the installer will then see the partition?  Don't know for sure, but I've done that and saved a step in the "Buntu" installation process on a standard HDD.

BTW, it might be useful to see a screenshot of your partition table.

---

### Post by AngryMuffin on 2015-05-27
> **Geoffrey_Arndt said:**
> BTW, it might be useful to see a screenshot of your partition table.

Below is how I have it partitioned, and I'm not sure why it doesn't detect the 16 GB separately (it detects just the whole disk as free space). I may try your method of GParted but for some people it seems to have mucked up their Windows partition, and unfortunately I don't have another computer to work on in the case I do break the Windows partition. I'll do some research before trying, thank you for your reply.

[IMG]http://i.imgur.com/qsTyeoi.png[/IMG]

---

### Post by oldfred on 2015-05-27
Since you have two drives, do not try to use Windows to boot Ubuntu. Keep Windows boot loader on sdb which is the one you boot Windows from and install grub to sda which is the default with Ubuntu. But still with two drives use Something Else to install, not any auto install options.

Plus you seem to be booting from sdb1 as system reserved, but your Windows install is on sda1. Did you have sdb drive as default boot in BIOS when you installed Windows to sda?

And since drives are MBR, you are booting in BIOS mode not UEFI. So be sure to always boot in BIOS mode not UEFI, if a newer system that has both.

Make a Windows repair flash drive or know how to boot into repair console on Windows installer, so you can repair Windows. Only minor repairs to Windows can be done from Linux.

 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

