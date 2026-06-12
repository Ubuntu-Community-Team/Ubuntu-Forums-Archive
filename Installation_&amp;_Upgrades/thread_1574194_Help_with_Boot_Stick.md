---
title: "Help with Boot Stick"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by Ivan Von Krieg on 2010-09-13
Hey guys... I just bought a new rig, and I'm using Windows 7 Professional.
But I feel that I must learn how to use Linux, and loooots of people told me to start with Ubuntu...
By the way, I'm from Brazil, so... English is my second language... I apologize for my grammar mistakes...
Anyway...
I want to create some sort of boot-stick, you know?
But I do not want to install Ubuntu, I want to run it directly from the  flash drive... And I want configure it to save all the changes directly  to the pendrive... I also want to use the newest (stable) 64 bits  version... And I want to create this stick through windows...
Seems easy, right?
But not only I don't know how to do it but I can't find info bout that...
Also, if it's easy I want to configure this "version" to use only ram and the flash drive I want to know how to do that too...
I have 12 gb of ram, so i think i don't need to use the hd for  anything... But I think I'll have to edit the source code to achieve  this objective, right?

---

### Post by rotave on 2010-09-14
Not sure if you can do that with Ubuntu. But I would try Puppy Linux 5. It's based off Ubuntu and can run off a USB flash drive, has the ability to save to the drive and runs in RAM only.

---

### Post by C.S.Cameron on 2010-09-14
Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you select the "Advanced" button and choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your hard drive, even when booting another computer.

---

