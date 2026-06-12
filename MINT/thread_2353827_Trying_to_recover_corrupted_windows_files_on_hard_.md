---
title: "Trying to recover corrupted windows files on hard drive using linux on the same PC"
date: 2017-02-25
forum: MINT
---

### Post by bunnyboo127 on 2017-02-25
Ok so first please go easy on me, I'm a real noob at using linux.
Is there any way that I can access that folder which was corrupted when I was running windows 10 on my laptop. I tried many ways to access my files but the only thing that worked was using a usb with a bootable linux mint 18.1
So my problem is that I can't open 'Users' located in /media/mint/OS/ to access my documents so I can copy them to my external hard drive.
Every time I try to open the folder, this message pops up: "Sorry, could not display all the contents of "Users": Error when getting information for file '/media/mint/OS/Users/Default User': Input/output error"

Please help me guys, thanks in advance!

---

### Post by howefield on 2017-02-25
Moved to the "*MINT*" forum.

---

### Post by oldfred on 2017-02-25
You probably did not turn off Windows fast startup or always on hibernation.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

The Linux NTFS driver will not mount hibernated nor NTFS needing chkdsk to prevent damage.
You may be able to manually force mount read only.


 Force mount, read only (ro), change example with sda3 to your correct NTFS partition:
sudo mkdir /media/windows
sudo mount -t ntfs-3g -o ro /dev/sda3 /media/windows

---

### Post by bunnyboo127 on 2017-02-25
So it kind of worked, but I can't still see my documents. I can only see the public files and some empty folders, what should I do?

---

### Post by oldfred on 2017-02-25
You can try testdisk and then possibly photorec.
But some suggest Windows tools work better on Windows NTFS.

 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk
[/URL]
 [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step) 

I have used photorec. 
It takes a very long time, you have to have another drive to copy data into, and it only recovers by extension(type), not full file name.

      
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam. 
     
If you thought you did not have time to create backups, issues like this teach us the importance of backkups.

 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by bunnyboo127 on 2017-02-26
Ok so I succeeded backing up my data, so what I want to do now is to install windows 10 again. Could you instruct me on how install windows 10 again using a bootable drive thru linux mint?

---

### Post by oldfred on 2017-02-26
This is a Mint sub-forum on Ubuntu. 
Do not know Mint, nor installing Windows. A few links that may help.

 Usb installer from Windows - pendrive may not work with UEFI
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows) 
      
 You can use Win32 Disk Imager to install Ubuntu to a USB pendrive from Windows.
[URL="https://wiki.ubuntu.com/Win32DiskImager/iso2usb"]https://wiki.ubuntu.com/Win32DiskImager/iso2usb
[/URL]
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media) 

[URL="https://wiki.ubuntu.com/Win32DiskImager/iso2usb"]
[/URL]

---

### Post by yancek on 2017-02-26
If you simply want to re-install windows 10 again, use the installation DVD/usb that you have and boot the computer with it and install.  As I understand your post, the only reason you are using Linux Mint is to recover data from your failed windows install and only want windows.  If you are having problems with the installer you would be much better off at a windows 10 or microsoft support forum as your question has nothing to do with Ubuntu or Linux.

---

