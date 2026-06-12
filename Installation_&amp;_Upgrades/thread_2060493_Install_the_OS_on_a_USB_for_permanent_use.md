---
title: "Install the OS on a USB for permanent use"
date: 2012-09-20
forum: Installation &amp; Upgrades
---

### Post by zootoxin on 2012-09-20
Hi all, 

I have tried googling this but I think there are too many install ubuntu/linux _from_ a usb stick instead of _to_

And that's basically my question is possible to boot from USB stick A to USB Stick B then run ubuntu as a normal installation. i.e saving files, programs etc. 

Thanks 

Zoot

---

### Post by davidbilla on 2012-09-20
Have you tried selecting USB drive B as your destination drive for OS installation when you boot from USB drive A?

---

### Post by zootoxin on 2012-09-20
> **davidbilla said:**
> Have you tried selecting USB drive B as your destination drive for OS installation when you boot from USB drive A?

yeah I couldn't work it out though so it failed.

How do I need to format the target drive on a windows machine?

I have very limited knowledge in linux things.

Also would I be able to/ would I need to partition the USB drive to enable storage space?

Thanks

---

### Post by grahammechanical on 2012-09-20
This link shows up to date pictures for using Startup disk creator:

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu")

You will find Startup Disk Creator in the Dash of an existing 12.04 installation or on a 12.04 Live CD or a 12.04 Live USB image.

Note section 6 in that link. Do you see the heading: Disk to Use. That should be the place to select another USB drive.

Note also the check box: Stored in reserved extra space - How much. That is where you create another partition on the USB drive that your settings and data to go in. so, that it is still available at every boot.

Startup Disk Creator will take care of the formating and partitioning.

The situation is different if you want the USB memory stick as a data drive that can be read by windows. In that case it should be formatted in Windows as FAT32 or something like that.

Regards.

---

### Post by C.S.Cameron on 2012-09-20
Following is step by step how I installed 12.04 on a 8GB flash drive on an Intel machine:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.
(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000 megabytes.
Location = Beginning.
"Use as:" = "FAT32 file system", (
And "Mount point" = /windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4000 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You can revise grub later, if you wish.

---

### Post by kurt18947 on 2012-09-20
Yes,  just format the target USB drive for a Linux file system, I used gparted.   I used ext2 in the belief that ext2 performs less write operations so may be faster and create less 'wear'.  I then installed xubuntu normally using the advanced drive options.  Mine works but it's substantially slower than a hard drive install.  I'm sort of intrigued by "USB3 flash drives".  It seems like read/write speeds may be more suitable for uses such as this even plugged into a USB2 port.

---

### Post by penreturns on 2012-09-20
When creating Live USB, select the persistent option. With persistent, you can install apps, save file etc. The file and apps will remain there unless you remove it. Refer  	 		 			 			 						 				 					 					 				
 												  				**[Create a Persistent Bootable Ubuntu USB Flash Drive]("http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/")**

---

### Post by kurt18947 on 2012-09-21
> **penreturns said:**
> When creating Live USB, select the persistent option. With persistent, you can install apps, save file etc. The file and apps will remain there unless you remove it. Refer                                                                                                                                              
                                                                   **[Create a Persistent Bootable Ubuntu USB Flash Drive]("http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/")**

The problem I've had with Live USBs is that they cannot be updated.  They're great for trials or for creating a permanent install.  I've tried installing updates on a Live USB and it has always failed within a couple updates.  "Real" installs on a USB drive seem to update okay.  My biggest complaint so far is that they're slow to load.  I didn't create a swap partition on the USB drive.  I use it for accessing secure web sites.  My thinking is that an install without flash or java (so far) and only used to access a few should-be-well-maintained web sites has less chance of having malware installed surreptitiously.  I use the regular install for normal everyday stuff like this site, youtube, etc.

---

### Post by zootoxin on 2013-03-12
> **C.S.Cameron said:**
> Following is step by step how I installed 12.04 on a 8GB flash drive on an Intel machine:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.
(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000 megabytes.
Location = Beginning.
"Use as:" = "FAT32 file system", (
And "Mount point" = /windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4000 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You can revise grub later, if you wish.

Hi, 

I followed this guide and it worked perfectly the only problem being a couple of months on and I am getting error messages all the time about how much room is left on the system drive (16gb USB)

Is there away I can solve this? 

I have made sure all files I don't need are deleted. 

Thanks 
Zoot

---

### Post by C.S.Cameron on 2013-03-12
Install gparted and have a look at this drive.
You should see how much of each partition is used.
With gparted you can expand the fuller partitions and shrink the ones with unused space.

---

### Post by zootoxin on 2013-03-14
> **C.S.Cameron said:**
> Install gparted and have a look at this drive.
You should see how much of each partition is used.
With gparted you can expand the fuller partitions and shrink the ones with unused space.

This is how my gparted looks could you please tell me how I can make things all better.

[IMG]http://roardesigns.co.uk/Help/gparted.PNG[/IMG]

Thanks

Zoot

---

### Post by kurt18947 on 2013-03-15
How much RAM do you have installed?  Do you hibernate(suspend to disk)?  I have one desktop with 4 GB. RAM and a notebook with 2 GB. RAM.  Neither has a swap partition or file and they both run great.  The only reason I could see for a 6.52 GB. swap partition - sdc4 - would be for hibernation.  I suspend to RAM rather than suspend to disk so no need for swap space.  I would shrink or eliminate the swap partition and enlarge the other two, especially sdc2.  If you want to know how much RAM your system is using, you could install htop from the repositories.  I sometimes have htop running in a terminal just to monitor RAM usage and I've never come close to needing swap.  An old beater notebook with 512 MB. RAM installed is another matter,  It has a swap partition and sometimes uses a bit of it.

---

### Post by C.S.Cameron on 2013-03-15
> **zootoxin said:**
> This is how my gparted looks could you please tell me how I can make things all better.

[IMG]http://roardesigns.co.uk/Help/gparted.PNG[/IMG]

Thanks

Zoot

Shrink sdc4 down to about 2GB and move to right.
Expand sdc3 to 4GB and move to right.
Expand sdc2 to use remaing free space

---

### Post by zootoxin on 2013-03-16
Can I make these changes on the fly or do I need to put the usb in another machine?

---

### Post by C.S.Cameron on 2013-03-16
> **zootoxin said:**
> Can I make these changes on the fly or do I need to put the usb in another machine?

You need to put the USB into another machine running Linux.

---

### Post by thefederer1 on 2013-04-02
can this be done through daemon tools, or is an install disc required?

---

