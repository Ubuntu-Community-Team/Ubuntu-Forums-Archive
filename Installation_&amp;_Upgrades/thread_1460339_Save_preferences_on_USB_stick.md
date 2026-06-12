---
title: "Save preferences on USB stick"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by Richbuntu on 2010-04-22
Hi,
I'm running Ubuntu from my USB stick (using UNetbootin).
Unfortunately every time I turn my computer off my personal preferences are deleted.
Can someone tell me how can I save my personal preferences on the USB stick, so I'll always be able to use them?

Thanks,
Richbuntu

---

### Post by cybrsaylr on 2010-04-22
Anyone?
This is something I was wondering how you do also.

---

### Post by C.S.Cameron on 2010-04-22
This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext3 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Windows, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

The home-rw partition is not necessary but is handy to have when upgrading versions of Ubuntu.
I have not had luck keeping the casper-rw partition when replacing the Ubuntu version with a newer one.

---

### Post by Richbuntu on 2010-04-23
I didn't understand what to do after using Unetbootin.
Can you try and explain it again?

---

### Post by jimmers on 2010-04-23
You could try this tutorial from UbuntuGeek:-

  	 	 	 	 	 	  I was reading [How to install Ubuntu Linux from USB Stick]("http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html") posted on this site a while ago, and found it to be quite some work to get Ubuntu working on a USB stick. Besides, having to prepare your USB device, creating a separate partition on it which will be more or less “useless” after the installation, giving up 750MB of space?  
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
 So you have finished the installation. However, when you will be restarting your system from USB, you will find out that the partition you just installed Ubuntu to cannot be mounted.
Here comes the trick:
 
[LIST=1]
[*]Once the 	installation is finished, reboot your PC (this is the safest) from 	your LiveCD, with your USB device connected;  	
[*]Once started, open 	up a terminal (Applications - Accessories - Terminal);  	
[*]In the Terminal, 	type: sudo -i (which will give you root privileges, so be careful 	from now on!);  	
[*]Change directories 	to /media/disk/boot/grub - This will take you to the “/boot/grub” 	directory on the USB device;  	
[*]open menu.lst with 	vi (make a backup first!)  	
[*]Go to line 130 (or 	somewhere in that area).
You will find a line looking like:
## 	## End Default options ##
And underneath it you will find three 	entries pointing to your Ubuntu you just installed:
title         	Ubuntu 8.04, kernel 2.6.24-16-generic
root        	(hd1,0)
kernel     	/boot/vmlinuz………
initrd       	/boot/initrd…….
quiet
(the above 5 lines repeat 3 times 	with slight differences)  	
[*][B]The magic 	trick is to change (hd1,0) into (hd0,0) for all these three 	entries.
[/B]Why? Booting from USB device makes your USB 	device hd0, in stead of hd1 at time of installation.  	
[*]Search for the 	line starting with “# groot=(hd1,0)” and change (hd1,0) to 	(hd0,0) - **Don’t delete the # at te beginning of this line!** 		
[*]Once you did this, 	you can optionally remove the remaining of the file
(everything 	underneath ### END DEBIAN AUTOMATIC KERNELS LIST);  	
[*]Save the file, 	make sure it is owned by root:ubuntu (chgrp ubuntu menu.* will do)  	
[*]Edit device.map 	(in the same directory) and change the mapping of hd0 to /dev/sdb.  	
[*]Reboot your machine, from USB, choose the 	Ubuntu installation from the Boot Loader and you are one happy 	person.  	
[/LIST]
 I guess that is it. If I missed something, please comment.
 Regards,
 depending on your Dist, you may not need part 2.


works for me, worth a try

---

### Post by C.S.Cameron on 2010-04-23
> I didn't understand what to do after using Unetbootin.

Once you have made the ext2 casper-rw partition and used UNetbootin to install ubuntu, you need to edit syslinux.cfg by adding <space>persistent thus:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- **persistent**.

syslinux.cfg is found on the root of the USB stick. 

If you are booting the thumbdrive press alt-F2, type gksu nuatilus and go to /filesystem then to /cdrom to find it.
you can use gedit to edit it.

If you are booting from the Live CD or an installed version of Linux, plug in the flash drive, click on it's icon and you should see syslinux.cfg. you won't need to be SU to edit it.

---

### Post by Richbuntu on 2010-04-26
Thanks for the explanation, but now I have a new problem.
My USB stick can't be found anymore in the boot menu.
Do you have any idea what I'm supposed to do?

P.S.
My default OS is Windows XP

---

### Post by wilee-nilee on 2010-04-26
Another method is if you can get on a ubuntu set up use the startup disk creator which will put the casper-rw in home. Then you build that 2nd partition as big as you want et2 name it casper-rw, then delete the casper-rw from Ubuntu home. This sis a way of getting around the 4 gig limit of the disk creator. You can also do a full install on a thumb if it is big enough, but be careful and make sure grub is pointed at the device. Cameron's instruction are right on. Mine are similar but using a different loader.

---

