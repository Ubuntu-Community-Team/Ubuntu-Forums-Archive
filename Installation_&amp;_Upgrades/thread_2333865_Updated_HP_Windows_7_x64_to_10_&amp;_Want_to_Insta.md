---
title: "Updated HP Windows 7 x64 to 10 &amp; Want to Install Ubuntu 16.04.1 Dual Boot"
date: 2016-08-14
forum: Installation &amp; Upgrades
---

### Post by 3lCp on 2016-08-14
HP laptop, updated from Windows 7 x64 to Windows 10 (standard BIOS) with two 500 GB hard drives & 8 GB RAM wanting to dual boot Ubuntu 16.04.1 but running into issues with the disk 0 / sda already having four partitions and quickly running out of knowledge!

I had previously deleted the HP Recovery partition on Disk 0 and shrunk C: volume so I had approximately 100 GB unallocated space for Ubuntu install but during Ubuntu install realized I still had the 3 partitions and so wasn't sure how to work around that with either drive.

So I extended the C: volume and removed the 100 GB unallocated space until I could figure out what and how to setup.


Here is where I'm at in Ubuntu install when have the option to install alongside Windows 10 or Something Else:

Install alongside Windows 10 looks like it will install on sdb / second hard (D:) drive which seems like it would be easy and I would be fine with that, only not sure if I will have any boot issues, or if this is even ideal, etc? Would it really be that simple?

[https://i.imgur.com/N4VeFkU.jpg](https://i.imgur.com/N4VeFkU.jpg)

When I select Something Else, these are the options I'm presented with, keeping in mind I removed the unallocated space I had previously made but removed due to already having 3 partitions on sda / disk 0 / C:

[https://i.imgur.com/BlfGvZt.jpg](https://i.imgur.com/BlfGvZt.jpg)

With this configuration, what is the best method to install and dual boot Ubuntu? sda & sdb, sdb only, should I setup partitions beforehand? 

Assistance is greatly appreciated, thanks!

---

### Post by deepakdeshp on 2016-08-14
This link fives a guideline. It is advisable to understand about multiboot and UEFI
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)

---

### Post by deepakdeshp on 2016-08-14
This link fives a guideline. It is advisable to understand about multiboot and UEFI

A wealth of information

[https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by RobGoss on 2016-08-14
Hello and welcome, Looking at your setup choosing to install **alongside Windows 10**, should work as intended, you can place your mouse cursor on the Ubuntu partition and **drag** it right to left to give that Ubuntu partition more space if needed. Choosing the install option with take you to the next screen and will allow you to configure the rest of your installation it's pretty straight forward and kind of hard to mess that up

If you wanted to setup your partition before hand you can also do that and when you begin your installation you would need to choose ( **something else**) and use that **unallocated** space that you created to install Ubuntu. Keep in mind you will also need to create a** swap partition, **as well and give it about **2-GB** or so of disk space.


How-to dual boot Ubuntu & Windows
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If your system is using UEFI then you might want to take a look at this guide
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2016-08-14
With two drives, often better to have Windows on one drive, fully bootable on its own from that drive and Ubuntu on the other drive fully bootable from that drive. Then set BIOS to boot Ubuntu drive and grub can boot Windows.

But grub only boots working Windows. Or Windows that is not hibernated nor needs chkdsk. 
In Windows 10, it had fast start up which is always on hibernation, and updates may keep turning it back on. Then from grub you cannot boot Windows and have to temporarily restore Windows boot loader to boot into Windows. Or NTFS has minor corruption needing chkdsk. Again grub cannot boot it, and you have to temporarily reinstall Windows boot loader.

But if each on own drive, you can easily use one time boot key often f10 or f12 and directly boot Windows and often get into its own repair console with f8. But still best to have Windows 10 repair/recovery flash drive.

       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[URL="http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html"]http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html

      [/URL]
 Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
    [URL="http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html"]
[/URL]

---

