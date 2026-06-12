---
title: "Windows 7 loads a black screen after ubuntu 13.01 installation"
date: 2013-05-21
forum: Installation &amp; Upgrades
---

### Post by nietzsche nemesis on 2013-05-21
It was my intent to dual boot windows 7 and ubuntu, but I made a  mistake. Instead of burning the installation disk to a DVD I mounted the  ISO to a virtual drive and started the installation process. When I  restarted my machine it of course couldn't finish the installation, as  the drive it was looking for did not exist. I then went back and burned  the installation files to a real disk, booted from in, and installed  ubuntu properly. Now windows 7 displays a black screen right before the  login screen. It loads just fine in safe mode, but will not ever finish  shutting down, nor run check disk upon boot. I also attempted to repair  the issue by running boot repair in ubuntu. This was the message I got  at the end. Thanks in advance for the help.

Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/5689035/](http://paste.ubuntu.com/5689035/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/grubx64.efi file!

The boot files of [The OS now in use - Ubuntu 13.04] are far from the  start of the disk. Your BIOS may not detect them. You may want to retry  after creating a /boot partition (EXT4, >200MB, start of the disk).  This can be performed via tools such as gParted. Then select this  partition via the [Separate /boot partition:] option of [Boot Repair].  ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

A broken Wubi has been detected. Please fix it this way:
[https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)

---

### Post by oldfred on 2013-05-22
If you have Windows 7 and not Windows 8, you will not have secure boot issues as that is only Windows 8.

And then you should not need the extra function of renaming files. Some Windows 8 systems have modified UEFI to only boot the Windows bootmgfw.efi. Boot-Repair then has a work around to rename that file to be grub2's secure boot shim file that has the Microsoft key and will also boot. Then grub boots the backup /EFI/Boot/bkpbootx64.efi        file which you now have.

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 
      
 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

I have not seen anyone with UEFI have the issue of where the files are on the drive. That is primarily for BIOS based USB boot drives that are very large.

Wubi does not work on gpt partitioned drives which all UEFI drives are. So you can just delete wubi from inside Windows.

If you directly boot Windows with its efi file then you may be able to run chkdsk or make other repairs. Otherwise you may need a Windows repair flash drive.
      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

