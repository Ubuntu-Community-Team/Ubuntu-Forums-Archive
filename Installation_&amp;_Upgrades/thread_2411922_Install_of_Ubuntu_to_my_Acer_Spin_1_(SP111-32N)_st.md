---
title: "Install of Ubuntu to my Acer Spin 1 (SP111-32N) stuck on grub2"
date: 2019-02-05
forum: Installation &amp; Upgrades
---

### Post by aradyan on 2019-02-05
[COLOR=#242729][FONT=Arial]It's been 2 days I've been unable to install Ubuntu OS on my Acer Spin One (SP111-32N) : I want to install it alongside Windows (dualboot). I've been using a USB flashdrive to install the OS.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]At each try the installation blocked at the installation of grub2 bootloader. I've tried using both manual partition (with 2 partitions ext4 and swap) and "Install Ubuntu alongside Windows Boot Loader".
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]When I reboot the PC to exit the install and switch back to Windows, the partition with Ubuntu seems installed and there another FAT32 partition with grub 2.02 on it. However when I want to boot to Ubuntu some kind of terminal appear and I don't know how to boot to Ubuntu.

I've also tried to do this install, reboot the computer when the install block at grub2 package, and then do a boot repair using "Try Ubuntu". The Boot Repair program blocked at "Repairing Grub. This may take several minutes".

Here is a boot info taken just before running the boot repair : [http://paste.ubuntu.com/p/3gCgb3CrpW/]("http://paste.ubuntu.com/p/3gCgb3CrpW/?fbclid=IwAR17vTWWUaHZTXaUsKhwq6WC59aIKcs7orilJtV93y8EniXdz9cAs3MxmCw")
And the partitions (gparted) after the unfinish installation :

[IMG]https://i.ibb.co/FW5Q3XG/51345991-1698750680224360-18445905283776512-n.png[/IMG]
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I've been doing some research and it seems that this problem is quite common, however each solution given by other user seems different and sometimes, as I'm a beginner in Linux OS, I havent been able to try them.

Thanks a lot for you help ![/FONT][/COLOR]

---

### Post by yancek on 2019-02-05
Acer machines generally require you to set a supervisor password in the BIOS and enable trust to install an OS other than windows.
Don't use the auto-install option of Installing Alongside.  Use the manual "Something Else" option.
Read the Ubuntu documentation on dual booting windows/Ubuntu UEFI at the link below.  
Which Ubuntu are you using, 18.04, 18.10 ??  Are you using the server version or the Desktop?  Your partitions are really small.  A default Ubuntu 18.04 Desktop install requires almost 8GB.  I'd suggest you delete all the partitions and use the manual option and just create one partition for the system.  You don't need a swap partition as a swap file is used.  If you do want a swap partition, use something smaller like 2GB.  Also, Grub2 doesn't install to a FAT32 partition.  The second FAT32 partition you see is likely the usb you are using. 

  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

