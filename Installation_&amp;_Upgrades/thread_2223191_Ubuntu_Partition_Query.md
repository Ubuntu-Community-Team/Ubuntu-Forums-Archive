---
title: "Ubuntu Partition Query"
date: 2014-05-09
forum: Installation &amp; Upgrades
---

### Post by gordon99 on 2014-05-09
I am hoping to install Ubuntu 12.04 for dual booting alongside Windows 7. My notebook, a HP Compaq Presario, uses all four primary partitions for Windows etc. and I understand I will need to free up the HP_Tools primary partition for use by Ubuntu. I  also understand I will  need to shrink the "C" drive partition to make space for Ubuntu. The general advice seems to be to do all this with the Windows Disk Management program and then reboot a couple of times to make sure Windows is still functioning as it should. Would someone kindly confirm that my understanding of what I need to do is correct.
 Will the Ubuntu installation process  recognize the available space and if so what will it put in the freed up primary partition and what will it put in the space made available in the "C" drive partition. I apologize if my questions are very basic but am trying to grasp what will be happening when I run the installation disk.

---

### Post by kc1di on 2014-05-09
I would suggest that you read [this page]("https://help.ubuntu.com/community/WindowsDualBoot") first. so you will understand dual booting.

---

### Post by gordintoronto on 2014-05-10
See Full Circle Magazine, issue 41, page 36. [http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by oldfred on 2014-05-10
So far your process seems correct.

Also really good backups are vital. Some reinstall Ubuntu after errors and the reinstall does not caution that it overwrites the entire drive. On a re-install always use Something Else or manual partition to reuse exiting partitions.

Default instal is / (root) and swap. With your configuration it will use the last remaining primary partition as an extended partition and create logical partitions. You may want to also shink Windows a bit more and make a shared NTFS data partition, but always have lots of extra room in NTFS system partition. 
Better to have a separate shared NTFS data partition and set Windows system parition c: drive as read only. But you have to do that before or after install with gparted. If after and using auto install you can shrink / to make space or create partitions in advance and use  Something else to chose which partition is / (root).

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by gordon99 on 2014-05-11
Thanks all for your information and answers. I am sure I will have more questions as I progress.

---

