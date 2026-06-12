---
title: "Xubuntu on USB"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by toloratedmeat on 2010-04-17
Hey, I just installed Xubuntu on my USB using the USB Startup Disk Creator.

I didn't want it with the Live CD crap on it. Like the option to install.

I want a fully fledged copy of Xubuntu, and its user environment to behave like a normal computer would. 

For example:
When files get modified, they stay modified. (persistency)
When files get added, they stay there. (persistency)
When files get removed, you'll never see them again. (persistency)

How can I get xubuntu to act like it's installed on a hard drive on my USB?

Thanks!

---

### Post by wilee-nilee on 2010-04-17
> **toloratedmeat said:**
> Hey, I just installed Xubuntu on my USB using the USB Startup Disk Creator.

I didn't want it with the Live CD crap on it. Like the option to install.

I want a fully fledged copy of Xubuntu, and its user environment to behave like a normal computer would. 

For example:
When files get modified, they stay modified. (persistency)
When files get added, they stay there. (persistency)
When files get removed, you'll never see them again. (persistency)

How can I get xubuntu to act like it's installed on a hard drive on my USB?

Thanks!

You can do a full install with the Live CD if the usb device is big enough. So a little more information would help like how big is it.

The disc creator has a persistent setting, and you can actually make it as big as you want. To do this you have to have the persistent installed then follow this tutorial.
[http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)

If you decide to do a full install be very careful, grub will probably be set to install into the hard drive inspite of the install being onto a usb. So the key is that on the last gui in the install is a advanced button click on it and make sure it is pointed at the device no partition numbers. For example if you install on sdb1 the grub goes to sdb.

---

### Post by Dayofswords on 2010-04-17
link linky link, link!

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

do the same, just with xubuntu

---

### Post by jimmers on 2010-04-17
Try this tutorial by Ubuntu Geek:-
  	 	 	 	 	 	  
I was reading [How to install Ubuntu Linux from USB Stick]("http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html") posted on this site a while ago, and found it to be quite some work to get Ubuntu working on a USB stick. Besides, having to prepare your USB device, creating a separate partition on it which will be more or less “useless” after the installation, giving up 750MB of space? 
There had to be a better way.
Together with a colleague of mine, I decided to figure out whether there could be an easier way to install Ubuntu on a USB device.
I found a way of doing it in a much simpler way… without creating the separate partition to store the LiveCD:
A couple of assumptions to take into account when going through this manual:
 
[LIST]
[*]My computer (Dell 	D820 [[COLOR=#006400]_laptop_[/COLOR]]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html#")) 	has 1 internal disk, devided into 3 partitions (dell utility - 	windows - Ubuntu 8.04)  	
[*]Just one USB 	device (in my case a 250GB harddisk  	
[*]BIOS configured to enable boot from internal 	HDD, CD/DVD and USB [[COLOR=#006400]_Storage 	device_[/COLOR]]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html#")  	
[/LIST]
 (I didn’t take screenshots, so I will be explaining a lot about the screens… It looks like a lot of work, but trust me: it is not, and it really is easy:smile:
 
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
[*]If there is 	anything to migrate from other installations on your [[COLOR=#006400]_computer_[/COLOR]]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html#") 	(most likely not), do whatever you want, and click Forward;  	
[*]**The next screen 	is important** - It is titled: “Ready to Install”. **Be 	careful here: before clicking on Forward, **make sure you [B]click 	on the “Advanced” Button!
[/B]This will open a new screen, 	giving you the option whether and where to install the bootloader. 	**Select your USB device** (in my case it was /dev/sdb) to 	install the bootloader to;
Exit this screen and click on Forward 	in the “Ready to Install” screen, which will be shown;  	
[*]The installation will be started now. Just be 	patient, grab a cup of coffee and come back 15 minutes later, your 	installation will be more or less finished by then.  	
[/LIST]
 Works for me

---

### Post by toloratedmeat on 2010-04-17
Hey jimmers. I'm trying your solution now. I'll report back on how its going when it finishes. It's at 37% at the moment.

---

### Post by toloratedmeat on 2010-04-17
Nope. Didn't work. Most of the dpkg functions failed.

---

### Post by C.S.Cameron on 2010-04-17
I would suggest checking the MD5SUM of the iso you used to make your Live CD.

---

### Post by toloratedmeat on 2010-04-17
jimmers, after installing it your way, I realised that it only boots on one machine. The machine that grub was configured on. Is there anyway to make it work on all machines?

EDIT: Plus if it does boot, it get reduced to shell. How do I get into the GUI via the shell?

EDIT again: menu.lst is blank at /boot/grub

---

### Post by C.S.Cameron on 2010-04-18
When I do a Full install I unplug the hard drive of the machine I am installing from and never have any problems.

---

