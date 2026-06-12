---
title: "Windows 7 cannot load after installing Ubuntu 14 dual boot"
date: 2015-11-03
forum: Installation &amp; Upgrades
---

### Post by alexshmmy on 2015-11-03
Hello to all,

I was using windows 7 to my Dell business desktop. The hard disk drive was 250 gb and i wanted to istall ubuntu 14 alogside Windows 7. It is a process that I have done to my older desktops and laptops and never experienced problems. 
So i partitioned the 250 gb hdd to 180 Windows, 60 ubuntu, 10 linux swap. the problem now is that in the grub menu all OS are appearing but I can not load to Windows 7 (the initial windows 7 screen is appearing for 1 sec after that nothing).

I used the Ubuntu Boot Repair program and the outcome can be shown in the following link

[http://paste.ubuntu.com/13096083/](http://paste.ubuntu.com/13096083/)

The outcome of the command "sudo fdisk -l" is 

> Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xef02e593

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     2050047     1024000    7  HPFS/NTFS/exFAT
/dev/sda2   *     2050048   341475327   169712640    7  HPFS/NTFS/exFAT
/dev/sda3       341475328   480587775    69556224   83  Linux
/dev/sda4       480587776   500117503     9764864   82  Linux swap / Solaris



If someone has an idea please let me know. Thank you very much in advance

---

### Post by oldfred on 2015-11-03
Grub only boots working Windows.

Your boot flag got moved from sda1 to sda2, but the bootmgr & BCD were also copied to sda2. Grub2's os-prober does not use boot flag, but Windows does if booting directly with Windows.

You may need to use Boot-Repair to temporarily reinstall a Windows boot loader and see if you can  use f8 to get into Windows repair console. You should really have a Windows repairCD or flash drive as well as the Ubuntu live installer to make repairs.

       f8 to get to repair install screen, if you can start to boot
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[URL="http://www.sevenforums.com/tutorials/681-startup-repair.html"]http://www.sevenforums.com/tutorials/681-startup-repair.html
[/URL]
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

[URL="http://www.sevenforums.com/tutorials/681-startup-repair.html"]
[/URL]

---

