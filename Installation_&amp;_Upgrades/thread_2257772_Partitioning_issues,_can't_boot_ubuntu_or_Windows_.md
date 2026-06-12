---
title: "Partitioning issues, can't boot ubuntu or Windows 7 after install (live boot works)"
date: 2014-12-22
forum: Installation &amp; Upgrades
---

### Post by blackbird34 on 2014-12-22
I installed Ubuntu on my brother's computer (a Dell Vostro). However it had more than 4 primary partitions  on an MBR partition table and I have got messed up, neither Windows 7 nor Ubuntu 14.04 will boot. Booting from USB works fine. 

Boot info script from Boot-repair:
[http://paste.ubuntu.com/9597068/](http://paste.ubuntu.com/9597068/)

When i choose to boot from the hard drive, there is no GRUB screen, only a Windows boot error (0xc000000e - a required device is inaccessible). I think in my attempts to repair it have come to nothing and even removed the 100MB Windows boot partition that used to be there. 

when i do sudo update-grub on the live system i get this: 
/usr/sbin/grub-probe: error: failed to get canonical path of /cow

[FONT=arial]as described here: [http://askubuntu.com/questions/207663/cannot-update-grub-with-paramters-on-live-usb](http://askubuntu.com/questions/207663/cannot-update-grub-with-paramters-on-live-usb)

Can someone help me recreate a working Windows boot partition? Or an Ubuntu /boot partition? Or anything that will make Ubuntu and Win7 start? I'm lost. 

Thanks. [/FONT]

---

### Post by oldfred on 2014-12-22
You cannot run grub updates on the live installer as that is trying to update the live installer. If you really want to run the updates, you have to chroot into your install.

But easier just to install grub to MBR and boot the Ubuntu you have installed.
You link shows the mount of the Ubuntu partition sda2 in your case and the install of grub to MBR.
But you had Boot-Repair and chose to install a Windows boot loader. You need to let it run the default and install grub to MBR.

Windows boot loader in MBR looks for partition with the boot flag, and then in the partition boot sector to find what Windows file to use to boot ntldr for XP, or bootmgr for Vista or later. And then from partition boot sector loads bootmgr and BCD to boot Windows. 

But you deleted the Boot partition for Windows that has bootmgr & BCD, and did not copy those files into the NTFS partition with boot flag now sda1. If sda1 is the rest of the install, but script does not show /Windows/System32/winload.exe. If that is there and script just did not show it, then you can use your Windows repairCD or Flash drive to do repairs to install bootmgr & create a BCD so Windows can boot. Test that with Windows boot loader then reinstall grub to MBR.

Do you have a Windows repair disk, or backup of the 100MB Windows boot partition so you have copies of bootmgr & BCD? That is the best & easiest way to fix Windows. It may also need chkdsk for other repairs also.

The repair console or f8 was also in the 100MB partition you deleted, but you can run from your separate Windows repairCD or flash drive. You cannot fix bootmgr & BCD from Linux.
 f8 to get to repair install screen
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)

---

### Post by blackbird34 on 2014-12-23
Thanks for your help oldfred. 

I didn't have my windows 7 pro dvd with me but (for information purposes, in case anyone else comes) I was able to repair the Windows boot partition with a Windows live USB. 

I got the ISO from here (it is not any use if you don't already have a product key) [http://www.mydigitallife.info/official-windows-7-sp1-iso-from-digital-river/](http://www.mydigitallife.info/official-windows-7-sp1-iso-from-digital-river/) and created the live USB with [TuxBoot]("http://tuxboot.org/download/").

Thus the Windows boot sequence was back in order, and i ran Boot-repair on the ubuntu live USB again and got the GRUB boot menu back. 

Phew.

---

### Post by oldfred on 2014-12-23
Glad you got it working. :)

---

