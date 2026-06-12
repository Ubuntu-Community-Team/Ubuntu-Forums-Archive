---
title: "[help] Cannot Detect Windows and more"
date: 2014-11-29
forum: Installation &amp; Upgrades
---

### Post by Sharkhead on 2014-11-29
Hi,
Recently I started java development and from few friends I got to know that ubuntu is much better for development rather than Windows. I did few attempts on trial(boot demo through DVD) and was really impressive. So I thought of having a dual boot option. While I said Install, it said it couldn't detect any other operating system. So I went for something else option. Over there it was all complicated stuff with partitioning and all.
See this screenshot. 
These are the partitions in my 1TB disk.
[ATTACH=CONFIG]258283[/ATTACH]

This is the window in the Install Wizard after I select 'Something Else'
[ATTACH=CONFIG]258284[/ATTACH]


After figuring out a bit, the DEV/SDA1 is blank and all other drives have data.
So when I select the Dev/Sda1 it says
[ATTACH=CONFIG]258285[/ATTACH]

So I need help on how to go ahead and Install Ubuntu with a dual boot option which it'll probably ask on pc startup and also without the current data on the disk being deleted.

Here is the screenshot from Win7.
[ATTACH=CONFIG]258286[/ATTACH]

Here, you can see, the E drive is blank.

Its a partition created while installing Win 7

I want to install Ubuntu in that drive. 

Please guide me. :)


Thanks,
Sharkhead

---

### Post by oldfred on 2014-11-29
DO NOT overwrite existing Windows sda1 or sda2. Besides the 100MB Windows boot partition is way too small.
Typically sda1 is Windows boot partition and sda2 is its main install, if BIOS boot (not new UEFI). Do not specify Windows partition for anything related to Ubuntu install. And combo box at bottom is showing sda1 for boot loader. That is terribly wrong, you need to install boot loader to sda not sda1. If you install to sda1, you will not be able to boot Windows without repairs.

You cannot install Ubuntu in NTFS formatted partitions, it needs Linux formatted, typically ext4.
Minimum install is / (root) with ext4 and swap which has no format.

These are similar, show screen shots so you have a better idea of what the process is. 
Please review and come back with more questions.
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

You must backup entire Windows install and best to also have a Windows repair flash drive. Most Windows repairs need the Windows repair tools, Linux tools only can do minor repairs to Windows.

      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)


   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Impavidus on 2014-11-29
Your E drive is empty, and I think this one is known to Linux as /dev/sda6. It's not clean and therefore Ubuntu cannot see it's empty. The easiest way to install Ubuntu should be by using Windows to delete sda6 (E drive), reboot a few times to let Windows do any checks it likes. When Windows has done all its checks, isn't hibernating or using fast boot (I don't think that's available on Win7) and properly shut down, the installer should detect Windows and offer an automatic install alongside, in the then unallocated space. The automatic install gives a pretty decent result. Make sure you have Windows recovery dvds and backups of your important files nonetheless.

Once you have installed Ubuntu, you can conveniently use sda3 and sda5 (D and F drives) as shared data partitions, to share data between Ubuntu and Windows.

---

