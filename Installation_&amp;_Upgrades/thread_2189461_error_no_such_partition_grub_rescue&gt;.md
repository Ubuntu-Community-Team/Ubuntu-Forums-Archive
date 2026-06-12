---
title: "error: no such partition grub rescue&gt;"
date: 2013-11-22
forum: Installation &amp; Upgrades
---

### Post by clairemwilhelm on 2013-11-22
I had windows 7 and Ubuntu installed on seperate partitions on my netbook. I deleted the Ubuntu partition as I am selling the netbook. Rebooted to get this error message. I looked in a couple of other threads which were older and tried their suggestions of: 'rootnoverify (hd 0,0)' this received an 'unknown command' message. I then tried 'set root=(hd 0,0)' which was accepted but 'makeactive' didn't. The suggestions after that all included using the the CD drive which I don't have as I'm on a netbook or a USB with Ubuntu installed which I don't have either and can't make because I don't have a different computer. Help would be much appreciated.

---

### Post by oldfred on 2013-11-22
You needed to install a Windows boot loader to the MBR before you deleted grub. The grub boot loader in the MBR needs the rest of grub in the Ubuntu partition to fully load.
You can use your Ubuntu live installer or a Windows repair flash drive to fix it. You can make a Widows repair flash drive from another computer if you have a friend with the same 32 bit or 64 bit version of Windows, or work or school.

You may be able to get grub to boot manually. 
makeactive is a Windows command and hd0,0 is grub legacy not grub2.

If Windows boot files are in sda1:

 set root=(hd0,msdos1)
chainloader +1
boot

If not sure where boot files are, this might show the BCD file:
       ls (hd0,1)/boot

You should always have another way to boot & repair your system. Both Windows & Linux.

 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

