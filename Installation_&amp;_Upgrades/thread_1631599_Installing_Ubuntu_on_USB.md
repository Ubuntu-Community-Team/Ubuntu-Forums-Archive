---
title: "Installing Ubuntu on USB"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by WickedShadow on 2010-11-26
I am trying to get ubuntu to work from a usb hard drive i have installed it normally and using unetbootin neither have worked the same thing happens i boot the usb and it comes up with a black screen and a blinking cursor at the top left.

I dont know if this could effect anything but im trying to save whats on the disk by making ubuntu be on another partition ive heard of it working but i dont know.

Anything would help.

-WickedShadow

---

### Post by C.S.Cameron on 2010-11-26
This can be the symptom of a bad iso download, check the MD5SUM.

Also confirm that the USB HDD is first in boot order in BIOS.

---

### Post by jimmers on 2010-11-27
Try This :-
From a previous tutorial

  	 	 	 	p { margin-bottom: 0.21cm; }a:link {  }  I was reading [How to install Ubuntu Linux from USB Stick]("http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html") posted on this site a while ago, and found it to be quite some work to get Ubuntu working on a USB stick. Besides, having to prepare your USB device, creating a separate partition on it which will be more or less “useless” after the installation, giving up 750MB of space?  
 There had to be a better way.
 Together with a colleague of mine, I decided to figure out whether there could be an easier way to install Ubuntu on a USB device.
 I found a way of doing it in a much simpler way… without creating the separate partition to store the LiveCD:
 A couple of assumptions to take into account when going through this manual:
 
[LIST]
[*] 	My computer (Dell D820 [[COLOR=#006400]_laptop_[/COLOR]]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html#")) 	has 1 internal disk, devided into 3 partitions (dell utility - 	windows - Ubuntu 8.04)  	
[*]Just one USB 	device (in my case a 250GB harddisk  	
[*] 	BIOS configured to enable boot from internal HDD, CD/DVD and USB 	[[COLOR=#006400]_Storage_[/COLOR]]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html#") 	device  	
[/LIST]
 (I didn’t take screenshots, so I will be explaining a lot about the screens… It looks like a lot of work, but trust me: it is not, and it really is easy:-)
 
[LIST=1]
[*]Insert the LiveCD 	into your computer;  	
[*]Connect your USB 	device;  	
[*]Boot your computer 	from the liveCD;  	
[*]Once Ubuntu is 	started, go to System - Administration - Partition Manager
This 	will open the Partion Editor. Select your USB device and delete all 	partitions on it. Click Apply and exit Partition Editor;  	
[*]Double Click the 	Install Icon. This will start the Installer;  	
[*]The Welcome Screen 	is shown. Choose your language and click Forward;  	
[*]Select your Time 	Zone and click Forward;  	
[*]Choose your 	Keyboard Layout and click Forward;  	
[*]The partitioner 	will be started, and you will be given the choice where to install 	Ubuntu. Choose Guided - Use entire disk, selecting your USB device 	(this will most likely be /dev/sdb, don’t choose /dev/sdb1!);  	
[*]The next sceen you 	will give your username/password information. Provide the required 	info and hit Forward;  	
[*] 	If there is anything to migrate from other installations on your 	[[COLOR=#006400]_computer_[/COLOR]]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html#") 	(most likely not), do whatever you want, and click Forward;  	
[*]**The next 	screen is important** - It is titled: “Ready to Install”. 	**Be careful here: before clicking on Forward, **make 	sure you[B] click on the “Advanced” Button!
[/B]This 	will open a new screen, giving you the option whether and where to 	install the bootloader. **Select your USB device** (in 	my case it was /dev/sdb) to install the bootloader to;
Exit this 	screen and click on Forward in the “Ready to Install” screen, 	which will be shown;  	
[*]The installation will be started now. Just be 	patient, grab a cup of coffee and come back 15 minutes later, your 	installation will be more or less finished by then.  	
[/LIST]
 


 I guess that is it. If I missed something, please comment.
 Regards,

---

### Post by C.S.Cameron on 2010-11-27
Jimmers:
I think your instructions are for 10.04, 10.10 is a bit different.

10.10 to 16GB USB:

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

