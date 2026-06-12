---
title: "What is persistence?"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by Roclemir on 2010-04-03
I'm about to install a version of Ubuntu onto a 32GB flash drive, I've downloaded are Universal USB installer that will do most of the work for me, however, it asks

Step 4: Select a persistence option for your USB

and the options are

1GB CASPER -RW
2GB CASPER -RW
3GB CASPER -RW
4GB CASPER -RW

What is persistence? am I better off having more (ie 4GB) since my flash drive is a 32GB drive?

---

### Post by sanderj on 2010-04-05
Persistence is the space on your USB key the will be used to store information, so that that information is still there after a reboot.

---

### Post by jimmers on 2010-04-05
Roclemir,

Hi, as Sanderj stated Persistence is the space where you save your Docs, whatever, the max usage space on your list is 4GB, and that is all Fat 32 will allow, so your 32 GB is wasted, but try this tutorial from UbuntuGeek:-

  	 	 	 	 	 	  I was reading [How to install Ubuntu Linux from USB Stick]("http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html") posted on this site a while ago, and found it to be quite some work to get Ubuntu working on a USB stick. Besides, having to prepare your USB device, creating a separate partition on it which will be more or less “useless” after the installation, giving up 750MB of space?  
 There had to be a better way.
 Together with a colleague of mine, I decided to figure out whether there could be an easier way to install Ubuntu on a USB device.
 I found a way of doing it in a much simpler way… without creating the separate partition to store the LiveCD:
 A couple of assumptions to take into account when going through this manual:
 
[LIST]
[*] 	My computer (Dell D820 [[COLOR=#006400]_laptop_[/COLOR]]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html#")) 	has 1 internal disk, devided into 3 partitions (dell utility - 	windows - Ubuntu 8.04)  	
[*]Just one USB 	device (in my case a 250GB harddisk  	
[*] 	BIOS configured to enable boot from internal HDD, CD/DVD and USB 	[[COLOR=#006400]_Storage 	device_[/COLOR]]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html#")  	
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
[*] 	Once the installation is finished, reboot your [[COLOR=#006400]_PC_[/COLOR]]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html#") 	(this is the safest) from your LiveCD, with your USB device 	connected;  	
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
 

 It worked for me on my 16 Gb drive, and it runs sweet as you like.

Try.

Jim :p

---

### Post by sanderj on 2010-04-05
jimmers,

I think your quoted description does a normal installation to a USB device.

If so: I've tried that in the past to a USB stick, and the performace was horrible; each few minutes the whole desktop would halt and grey out for 10 - 30 seconds, and then become responsive again. My hypothesis: my USB stick was too slow to be handled as a normal drive.

On the other hand, a live-USB-stick is not a normal insallation; I think it regards the USB-stick as a slow, fixed device (just like a CD), and takes care of that by reading only once the live-USB-stick and putting as much as possible into RAM. That way the booted system stays responsive.

It could be a USB *disk* is fast enough for a normal installation, but I feat a USB *stick* is not fast enough for a normal installation. And thus you need the "usb-creator-gtk" to create a live-USB-stick, which seemed to be maxed to 4GB persistence size.

---

### Post by jimmers on 2010-04-07
I have never had any gray outs, and I am using the flash drive as I write, but you could try this tutorial from an other thread:-
  	 	 	 	 	 	  **Create a larger casper-rw loop file in Linux**

  The following tutorial explains how to *create a larger casper-rw loop file* for your Ubuntu based [[COLOR=#009900][FONT=Lucida Grande, Verdana, Arial, Sans-Serif][SIZE=2]_flash drive_[/SIZE][/FONT][/COLOR]]("http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/#") install. For example on: Ubuntu, Xubuntu, Kubuntu, Crunchbang or Linux Mint. A larger casper-rw loop file is particularly useful for those who have performed a Linux install to a large thumb drive using a Windows USB tutorial and need more persistent [[COLOR=#009900][FONT=Lucida Grande, Verdana, Arial, Sans-Serif][SIZE=2]_storage space_[/SIZE][/FONT][/COLOR]]("http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/#") for saving changes. The default casper-rw loop file we used in the Windows USB installation tutorials is only 1GB.
 **[COLOR=#800000]Notes:[/COLOR]** You will need to perform the following steps from a booted Linux system other than the USB Linux installation. I typically boot from the Live CD and then (once the system is up and running)  insert the USB flash drive that contains my Linux install and small casper-rw.
 **[COLOR=#800000]Warning:[/COLOR]** Block [[COLOR=#009900][FONT=Lucida Grande, Verdana, Arial, Sans-Serif][SIZE=2]_file size_[/SIZE][/FONT][/COLOR]]("http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/#") must be less than < 4096 MB on a fat32 formatted flash drive due to the 4GB file size limitation of a fat32 partition.
 **Creating a NEW larger casper-rw loop file**

 The following method will create a NEW casper-rw file that will replace the old one. If you want to resize an existing image see the next section**.**
 
[LIST=1]
[*]After your up and 	running in Linux, insert the flash drive that contains your 	**casper-rw** loop file  	
[*]Open a terminal  	
[*]Type the following into the terminal window 	and press enter
 	[INDENT]**dd if=/dev/zero of=casper-rw 	bs=1M count=****[COLOR=#ff0000]1024[/COLOR]**[/INDENT] 	(replacing **[COLOR=#ff0000]1024[/COLOR]** 	with the "size in MB" you wish to use for saving changes 	persistently)  	
[*]Type the following into the terminal and 	press enter
 	[INDENT]**[COLOR=#000000]mkfs.ext3 	-F casper-rw[/COLOR]**[/INDENT]
[*]Copy the new 	**casper-rw** file to your USB flash drive  	
[*]Restart your computer, booting from the USB 	flash drive and enjoy using the larger casper-rw loop block file you 	have just created.  	
[/LIST]
 **Resize an existing casper-rw loop file**

 The following method will allow you to *resize your existing casper-rw* image (expand casper-rw). You should create a backup just in case before proceeding.
 
[LIST=1]
[*]After your up and 	running in Linux, insert the flash drive that contains your 	**casper-rw** loop file  	
[*]Open a terminal 	and change directory (CD) to the location of your casper-rw file  	
[*]Type the following into the terminal window 	and press enter
 	[INDENT]**dd if=/dev/zero bs=1M count=****[COLOR=#ff0000]1024[/COLOR]**** 	>> casper-rw**[/INDENT] 	(replacing **[COLOR=#ff0000]1024[/COLOR]** 	with the size in MB you wish to increase the original size by)  	
[*]Type the following into the terminal window 	and press enter
 	[INDENT]**resize2fs casper-rw**[/INDENT]
[/LIST]
 If all goes well, you should now have a larger casper-rw loop file to use for saving your persistent changes.


I can't vouch for the above, as I have never used it, using the previous tutorial is the only way!!! I can utilise all the free space on my flash drive.
By the way my flash drive is a Kingston Data Traveller, I have tried other makes, but this brand is by far the best so far.

Good Luck

Jim

---

### Post by jeffrey246 on 2010-05-06
I have kubuntu. Some people in the past asked how to delete casper-rw so they don't have to replace the whole os. Here is a hint I have used several times so far has worked.  I save an old casper-rw to my computer hard drive. When I kill my os, I just replace the casper-rw with the old (working one). I get back all my desktop, downloads, my pass word, etc.
Jeff

---

