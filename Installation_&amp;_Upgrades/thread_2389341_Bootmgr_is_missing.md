---
title: "Bootmgr is missing"
date: 2018-04-15
forum: Installation &amp; Upgrades
---

### Post by haramara on 2018-04-15
Hello

I am trying to install Ubuntu on my computer on which previously Windows 7 was installed. I am using a usb stick which I have already successfully used for installing Ubuntu on another machine. The installation works fine and I erased the whole hard drive, but when I reboot the message "bootmgr is missing" is shown.

I have used boot-repair and this is the file it gave me: [http://paste.ubuntu.com/p/ZQtNSDYPNh/](http://paste.ubuntu.com/p/ZQtNSDYPNh/)

I would be happy to get some help.

Kind regards

---

### Post by yancek on 2018-04-15
You did not install the Ubuntu Grub bootloader and have windows boot code in the MBR of sdb, the 300GB drive.  That drive has only one partition and it is a windows filesysterm so you haven't installed Ubuntu anywhere.  When you install Ubuntu, make sure it is pointing to sdb (300GB drive) and make sure you install Grub to the MBR.  It  should detect your windows and create a menuentry in the Grub boot menu.

The error:  bootmgr is missing is a windows error as the file bootmgr is a windows only file.  Boot repair generally shows the Ubuntu and windows boot files but it doesn't show your windows boot files?

---

### Post by haramara on 2018-04-15
[FONT=arial]Thank you for your reply. I guess I made a stupid mistake and left my installation usb stick in the usb slot. Now after I removed it the system starts perfectly fine.

But I have one last question:

I executed boot-repair again and I am wondering whether this might cause problems:[/FONT][FONT=arial]

> 
Windows 2000/XP/2003 is installed in the MBR of /dev/sdb.

[/FONT]> [FONT=arial]sdb1: 
File system:       ntfs
Boot sector type:  Windows 7/2008: NTFS[/FONT][FONT=arial]

[http://paste.ubuntu.com/p/xz4vwwvPdq/](http://paste.ubuntu.com/p/xz4vwwvPdq/)[/FONT][FONT=arial]

Kind regards[/FONT]

---

### Post by yancek on 2018-04-15
Not sure what your question is.  You have windows code in the MBR of sdb and a windows system installed on sdb1, first partition of that drive.  That's the way it should work.  The only other drive showing is your usb/flash drive with the Ubuntu installer.

OK, I just took a look at your new boot repair link.  You made a mistake of installing Ubuntu UEFI while you have windows 7 as a Legacy/MBR install.  You either need to reinstall Ubuntu in Legacy mode or when you want to boot windows, you will have to change boot priority in the BIOS each time.

You might take a look at the Ubuntu documentation below which tells how you will know if you are booting in UEFI mode or Legacy mode.  It also explains converting from EFI to Legacy mode which might be easier than installing again.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by haramara on 2018-04-16
[FONT=arial]Actually there is no Windows 7 installed on the system anymore. I erased it from sda, where now Ubuntu is installed.

So I thought when I erased Windows 7, which indeed was using the BIOS mode, my system is ready to install Ubuntu in UEFI mode. 

From my last boot-repair report ([http://paste.ubuntu.com/p/xz4vwwvPdq/](http://paste.ubuntu.com/p/xz4vwwvPdq/) yesterday's report) It seems for me that sda now looks fine. 

But the following lines made me a bit worried:

[/FONT][FONT=arial]>  => No boot loader is installed in the MBR of /dev/sda.

Do I need a boot loader there?


>  => Windows 2000/XP/2003 is installed in the MBR of /dev/sdb.

Will this cause problems? Or should I replace it?


> sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS[/FONT]

Should I use a different file system or is ntfs fine? Will it cause problems that Windows 7/2008 is the boot sector type?



Thanks for your help so far.

---

### Post by oldfred on 2018-04-16
BIOS boot uses MBR, UEFI boot uses the ESP - efi system partition, so no UEFI boot files in MBR.

Having a BIOS boot loader in MBR is not an issue unless you attempt to boot it and the rest of the system is not there. If later you install another system to sdb in BIOS boot mode it will overwrite the code in the MBR.

While you can use NTFS, evenually it will need defrag and if incorrectly unmounted or other issue will need chkdsk. Neither of those fixes can be run from Linux. Or you should have Windows if using NTFS or at least a Windows repair disk so you can run repairs.

       Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm) 
   [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive](http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive)

---

### Post by haramara on 2018-04-16
Thank you oldfred for your background information. 

To be honest I feel not comfortable using NTFS, since I also heard that it might be not the best choice for Linux. 

Now  nothing is stored on that hard drive yet. Even though I do have a  Windows 7 copy I feel better with changing the file system. 

Can you tell me how I can do this or what guide I should follow? If necessary I can reinstall the whole system.

---

### Post by oldfred on 2018-04-16
You have UEFI hardware, so probably better to use UEFI install.
How you boot install media UEFI or BIOS is then how it installs.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Lot more info in link in my signature below (perhaps too much).

If new user a default install, but not using LVM nor full drive encryption as LVM is an advanced volume management system. Mostly for servers, but required if you must have full drive encryptions. It erases everything.

Default install of 16.04 uses just / (root) and swap. Newer versions do not create swap partition, but just have swap file. If UEFI you will also have the ESP - efi system partition, typically as first partition. Drive has to be gpt partitioned, not the old MBR(msdos) partitioning.

---

