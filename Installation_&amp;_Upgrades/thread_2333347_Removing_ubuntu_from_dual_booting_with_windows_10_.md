---
title: "Removing ubuntu from dual booting with windows 10 1607"
date: 2016-08-09
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2016-08-09
Yesterday I tried unity 8 in ubuntu 16.04, didn't work.  I rebooted to unity 7 and it was messed up.  Rebooted to windows 10 and went into disk management, deteled ubuntu volumes, partiitons and extended c: to recoup drive space.  When I rebooted I got a grub rescue prompt?  Why? I completed removed ubuntu and it partitions.  Had to fresh install windows 10.  I want to install ubuntu 16.04 again, alongside windows, but I need to be sure if ubuntu breaks, I can remove it without messing up windows.

Henry

---

### Post by oldfred on 2016-08-09
If UEFI, just go into UEFI boot menu, often f10 or f12 and boot Windows.
If BIOS you have to restore the Windows boot loader to MBR before removing Ubuntu.

But you always should have a Windows repair or Ubuntu live installer for current version of systems installed to make repairs.

         Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by grahammechanical on 2016-08-09
By deleting the Ubuntu partitions you removed Ubuntu but you did not remove the Ubuntu boot loader (Grub). That was still installed and it was looking for its configuration files on the Ubuntu partition but it could not find them. So, Grub dropped into rescue mode.

You sound like a person who should be experimenting with Ubuntu by using a Windows Virtual Machine (VM). Then you can delete the VM and start another VM whenever you like without messing with partitions.

Or, if you find that Ubuntu gets messed up in some way, then re-install Ubuntu using the Something Else option that will let you re-use the existing Ubuntu partitions.

Or, if you want to remove Ubuntu you might try OS uninstaller which we install and run from a Ubuntu live session.

[https://sourceforge.net/p/os-uninstaller/wiki/Home/](https://sourceforge.net/p/os-uninstaller/wiki/Home/)

I think that OS uninstaller is part of Boot Repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Oh, like you I have found that Unity 8 session is not working yet but installing it and attempting to use it has never messed up Unity 7 even when I have to power off to get out of a non working Unity 8 session.

Unity 8 does not work with proprietary video drivers. Could that be the reason it was not working for you?

Regards

---

