---
title: "Problems on installling ubuntu  10.04 to USB stick.."
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by Guitar-maniac on 2011-01-19
I tried installing ubuntu 10.04 to 8g Kingston stick witn usb-creator as suggested by the ubuntu wiki. It just stopped in about 15%, terminal didn't say any error, just went back to the mode when you can write in it.
 
I tried with another stick but the same thing happened, i installed them both from 10,04 livecd. After that i tried unetbootin, it downloaded the 10,04Live iso and that (seemed to) went through, rebooted my pc and switched removable as a boot device from bios. After the boot my pc just said Boot error. 
There was no other usb stick on my computer atm, and i checked from BIOS the removable boot order, and there was only one visible so it had to be that one.

---

### Post by C.S.Cameron on 2011-01-19
Sometimes in BIOS the flash drive just shows up as another hard drive, in which case it should be made the first hard drive.

---

### Post by Skaperen on 2011-01-19
I've had periodic problems with USB memory sticks being the install target on my ASUS EeePC.  Maybe it is because I had also booted the installer from another USB memory stick (e.g. there are two of them plugged in).  I have not had the problem installing to an SDHC card, though (a 16GB one).

---

### Post by jimmers on 2011-01-19
Try this tutorial 

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

