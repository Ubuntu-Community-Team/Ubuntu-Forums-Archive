---
title: "problem with ubuntu 10.10 installed on USB"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by allsystems on 2010-12-14
Hello,iv installed ubuntu 10.10 onto a usb 4gb pen. EVerything works fine. However I then wanted to encrypt the USB using truecrypt inside ubuntu and got an error message telling me it could not find some file. I then installed virtualbox onto the ubuntu this installed fine,i then installed windows xp and after completion clicked save the state. I then restarted ubuntu and when it loaded up again the virtualbox and windows xp had been deleted. Iv tried this twice just to make sure but same thing both times. Would really appreciate any help regarding this. I really need to get this sorted within the next few days,thanks

---

### Post by sanderd17 on 2010-12-14
I wonder if 4GB is enough for Virtualbox and XP. If it isn't enough, ubuntu can just delete files (or rather: only save them in RAM) since it's a life usage, not an installed distro.

---

### Post by ajgreeny on 2010-12-14
Have you actually installed ubuntu to the USB, or is it just a live system on there?  It sounds like the latter, which would explain why VB has gone.

I agree, however, that 4GB is probably not enough for both OSs.

---

### Post by allsystems on 2010-12-14
how do i check if ubuntu is installed or just a live install?Also I purchased 4gb because i read somewhere that it cant support any higher than 4gb of udb install,please help

---

### Post by sanderd17 on 2010-12-14
> **allsystems said:**
> how do i check if ubuntu is installed or just a live install?Also I purchased 4gb because i read somewhere that it cant support any higher than 4gb of udb install,please help

4GB is the max for live USBs. But I think you don't want a live install. I guess you want a permanent install.

Could you explain why you want to install it on USB and why you need xp to be on it? Maybe we can give other options to work around your problem.

EDIT: how do you check: do you have an "install" link on your desktop? That says ubuntu isn't installed yet.

---

### Post by efflandt on 2010-12-14
How did you "install" Ubuntu on the USB.  It sounds like you just have the **live/install iso** on it.  In that case the 4 GB limit is the size of persistent data, which is actually a loop mounted file system within a file called casper-rw.  But the USB itself is a FAT32 file system which has a 4 GB file size limit.  But if you did not set up persistent data however you installed the iso on USB, then maybe there is no persistent data, and that is why things you install are only temporary, and disappear when you shut down.

While live/install iso on USB is useful for testing or installing Ubuntu, it is somewhat limited for regular use, because you cannot do things like kernel updates or install video drivers or anything else during initial boot, since that is fixed and cannot be changed (unless you create your own iso file first).  And it has virtually no security (auto logs in as default user ubuntu, who can do anything using sudo).

If you do a regular install to USB, using a regular Linux file system, the size if files or the system is limited only by the size of the file system, and the file system size is limited only by the size of your USB device.  However, 4 GB is minimal for a regular install and would not leave you with much room (8 GB or larger is recommended).

If you do a regular install of 10.10 to USB, you have to use the **manual partitioning** option, and for USB flash it would probably be best to use ext2 file system (the journal of ext3 or ext4 would do more writing).  **Pay attention to the bottom of that screen**, and select your USB device for the location to install grub (that is in a different place for 10.04 or earlier versions).

---

### Post by allsystems on 2010-12-14
> **sanderd17 said:**
> 4GB is the max for live USBs. But I think you don't want a live install. I guess you want a permanent install.

Could you explain why you want to install it on USB and why you need xp to be on it? Maybe we can give other options to work around your problem.

EDIT: how do you check: do you have an "install" link on your desktop? That says ubuntu isn't installed yet.


Hello,Yes when I boot up the usb there does be an option that say "install". I installed it using the usb universal installer. I think you are right in that it is not a proper installation. I want to have linux OS onto a usb which I can plug in and load up like a normal usb and boot it up like a normal operating system. I then want to using virtualbox to install windows xp since this is an operating system that I mainly use. This file has to be encrypted.

---

### Post by allsystems on 2010-12-14
> **efflandt said:**
> How did you "install" Ubuntu on the USB.  It sounds like you just have the **live/install iso** on it.  In that case the 4 GB limit is the size of persistent data, which is actually a loop mounted file system within a file called casper-rw.  But the USB itself is a FAT32 file system which has a 4 GB file size limit.  But if you did not set up persistent data however you installed the iso on USB, then maybe there is no persistent data, and that is why things you install are only temporary, and disappear when you shut down.

While live/install iso on USB is useful for testing or installing Ubuntu, it is somewhat limited for regular use, because you cannot do things like kernel updates or install video drivers or anything else during initial boot, since that is fixed and cannot be changed (unless you create your own iso file first).  And it has virtually no security (auto logs in as default user ubuntu, who can do anything using sudo).

If you do a regular install to USB, using a regular Linux file system, the size if files or the system is limited only by the size of the file system, and the file system size is limited only by the size of your USB device.  However, 4 GB is minimal for a regular install and would not leave you with much room (8 GB or larger is recommended).

If you do a regular install of 10.10 to USB, you have to use the **manual partitioning** option, and for USB flash it would probably be best to use ext2 file system (the journal of ext3 or ext4 would do more writing).  **Pay attention to the bottom of that screen**, and select your USB device for the location to install grub (that is in a different place for 10.04 or earlier versions).

Hello,yes you are right i think i just have alive install and not an proper install. I really do appreciate your post but I havnt understodd anything about what you have said. I am not too technical but can follow step by step instructions. Is there a tutorial or step by step to do a proper install of ubuntu onto a usb drive so that when I install something it saves. Id really appreciate the help

---

### Post by allsystems on 2010-12-14
also wondering do I need to buy a disc that has ubuntu OS on it or can i download it. I kindof understand what you are saying,basically i will have to create a bottable usb drive with ubuntu OS on it. Only information I how do I install a regulur ubuntu onto the USB.Also once this is done any programs I use on ubuntu will these be saved automatically like a regular OS.I appreciate all the help
ps;is ubuntu linux the norm for linux operating system on usb?

---

### Post by C.S.Cameron on 2010-12-14
I do not think you will have much luck with with XP inside Vbox with a Full install on 4GB. Ubuntu takes about 2 1/2 GB which does not leave much for Vbox and XP. I have had XP in Vbox working with a persistent install on 4GB, but there was not room to install SR3.

Step by step for a Full install of 10.10:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
(Optional partition for use on Windows machine)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 4GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 6 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 8 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB, same size as RAM), Beginning and "Use as" = "swap area" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by allsystems on 2010-12-15
hello,il give this a shot first thing tommorow morning

---

### Post by allsystems on 2010-12-15
hello,the method told works great. Only question is I want to install windows 7 ultimate onto the USB stick also,this will be inside the partition where ubuntu is installed,il install windows 7 using virtualbox,only question which partition needs to be made larger. The windows 7 is 3gb itself. I also am now purchased a 16gb usb pen

---

### Post by C.S.Cameron on 2010-12-15
Make /home larger, the vdi ends up there. 
(Show hidden files).

Edit:
I keep a Windows 7 vdi by itself on a separate 8GB flash drive.

---

