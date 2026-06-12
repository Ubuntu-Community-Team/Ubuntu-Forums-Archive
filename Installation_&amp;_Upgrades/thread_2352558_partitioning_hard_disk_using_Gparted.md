---
title: "partitioning hard disk using Gparted"
date: 2017-02-13
forum: Installation &amp; Upgrades
---

### Post by HDD on 2017-02-13
I have 500 gb hard disk with no partition & ubuntu16.04 installed ,i want to install windows10 along with ubuntu for that i want to divide my hard disk into parts of 225GB each,i have made boo

table usb & downloaded Gparted ,please advice how to make partition Hard disk as the current single partition is Root also, please advice how to proceed




[ATTACH=CONFIG]273685[/ATTACH]

---

### Post by yancek on 2017-02-13
From GParted on the usb, turn swap off then delete it and the Extended partition (sda2).  Then highlight sda1 and make sure it is not mounted and click on the partition tab at the top of the window and select resize and shrink to the size you want.  Create another swap in this space (if you want) and leave the rest of the unallocated space for windows.  Make sure you have the Ubuntu DVD/flash drive so you can reinstall Grub after installing windows.

---

### Post by RobGoss on 2017-02-13
Hello and welcome, I would recommend installing** Windows 10** first, The reason I say this is because Windows has a **MBR** partition and that's were the boot loader for Windows will resides. Installing Ubuntu first will surely mess up your boot up for Windows

After installing Windows you can then create a partition to install Ubuntu on using the **disk management tool **for Windows, it's much easier to create partitions with that tool. After you've done that you can install Ubuntu as a dual boot if needed

I'm sure there's more advice to be shared about this process

---

### Post by oldfred on 2017-02-14
You have primary partitions available.
You should just be able to shrink the ext4 partition and create a new NTFS partition as sda2 and add boot flag.
While Windows BIOS installs typically use two primary partitions they can install to just one.

But make sure you know how to use Windows repair console from installer or make a Windows 10 repair flash drive.
Make sure you turn off Windows 10 fast start up or always on hibernation.

Linux tools will not see nor mount a hibernated NTFS partition nor a NTFS partition that needs chkdsk. And you cannot fix those from Linux, nor will grub then boot that broken Windows. So to repair Windows you must temporarily reinstall Windows boot loader, fix Windows and then use Ubuntu installer to restore grub to MBR. Windows on major updates may turn fast start back on, so after updates make sure fast start is still off.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

