---
title: "Install on usb and run"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by telmore007 on 2010-04-06
I've tried searching here and google. So far no luck. I want to install ubuntu on a flash drive to use at work. I can make a live copy on a flash drive, but I cannot figure out how to install and run from a flash drive. I have a 16 gb and a 4gb flash drive. All I care to do on the system is for internet(facebook apps), email, and open office. 

Thanks for the help. :)

---

### Post by phillw on 2010-04-06
Hi,

if you are using 9.04, then head over to [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Ubuntu 9.10 versions  have 'USB Start Up Disk Creator' available from the system menu where you find things like synaptics.

Persistance can only 'see' 4GB, you can still use a larger USB stick, but you need to format the extra area up as a another partition. A little tip for the drives, do not allocate all 100% of the space it sees for persistance, hold a little back (I use 100MB) It just seems to be happier that way (I was told there was a reason, but cannot recall it).

You may want to ensure the system you wish to boot with the USB device actually supports it --> [http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/](http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/)  has the instructions of checking the computer.

Regards,

Phill.

---

### Post by telmore007 on 2010-04-06
Ok, I've done that. But I cannot save anything. Like to install flash for facebook apps. When it starts up, I can run live or install. I only want to run it live. Would I have to install say "flash" every time I use it?

---

### Post by jimmers on 2010-04-07
You could try this tutorial by UbuntuGeek:-

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
 So you have finished the installation. However, when you will be restarting your system from USB, you will find out that the partition you just installed Ubuntu to cannot be mounted.
Here comes the trick:
 
[LIST=1]
[*]Once the 	installation is finished, reboot your [[COLOR=#006400]_PC_[/COLOR]]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html#") 	(this is the safest) from your LiveCD, with your USB device 	connected;  	
[*]Once started, open 	up a terminal (Applications - Accessories - Terminal);  	
[*]In the Terminal, 	type: sudo -i (which will give you root privileges, so be careful 	from now on!);  	
[*]Change directories 	to /media/disk/boot/grub - This will take you to the “/boot/grub” 	directory on the USB device;  	
[*]open menu.lst with 	vi (make a backup first!)  	
[*]Go to line 130 (or 	somewhere in that area).
You will find a line looking like:
## 	## End Default options ##
And underneath it you will find three 	entries pointing to your Ubuntu you just installed:
title Ubuntu 	8.04, kernel 2.6.24-16-generic
root (hd1,0)
kernel 	/boot/vmlinuz………
initrd /boot/initrd…….
quiet
(the 	above 5 lines repeat 3 times with slight differences)  	
[*][B]The magic trick 	is to change (hd1,0) into (hd0,0) for all these three entries.
[/B]Why? 	Booting from USB device makes your USB device hd0, in stead of hd1 	at time of installation.  	
[*]Search for the 	line starting with “# groot=(hd1,0)” and change (hd1,0) to 	(hd0,0) - **Don’t delete the # at te beginning of this line!**  	
[*]Once you did this, 	you can optionally remove the remaining of the file
(everything 	underneath ### END DEBIAN AUTOMATIC KERNELS LIST);  	
[*]Save the file, 	make sure it is owned by root:ubuntu (chgrp ubuntu menu.* will do)  	
[*]Edit device.map 	(in the same directory) and change the mapping of hd0 to /dev/sdb.  	
[*]Reboot your machine, from USB, choose the 	Ubuntu installation from the Boot Loader and you are one happy 	person.  	
[/LIST]
 I guess that is it. If I missed something, please comment.
Regards,

Works for me on a Gateway DataTraveler 16Gb, I am using as I write.


Jim

---

### Post by jeffjanzen on 2010-04-12
wow. thanks for the step-by-step.
this conflicts with some other advice i've gotten from various forms of ubuntu documentation, but i'm going to give it a try, because nothing else works.

1. i thought partition numbering started with 1 even though drive numbering starts with 0 (i.e. sdb1=hd1,1)

2. i told the installer to put the bootloader ("loader") on sdb1 instead of just sdb. maybe that was causing as problem?


UPDATE: Yes, that was the problem, and the other discrepancy is because i'm using grub2. with grub2, partition numbering starts with 1, not 0. and menu.lst has been replaced by grub.cfg. also, with grub2, the hd specification doesn't seem to matter. (I'm still trying to figure that one out.) It seems to find my flash drive whether i specify hd0 or hd2. On the other hand, my result is not ideal: it shows the glowing grayscale ubuntu logo, but it's not loading gnome for me. just gives me a command line. and when i try startx, it says there's "no screen found". still working on that one...

---

### Post by Herman on 2010-04-12
:)  I agree with jimmers, it's easier, and better to just install Ubuntu in your flash memory stick as a regular installation.

If you're using a modern version of Ubuntu, you can skip part 2 of that how-to, because you'll be booting with UUID numbers and using an /etc/fstab file with UUID numbers.

With this kind of installation, (with a modern version of Ubuntu), you'll be booting with GRUB2, so if you ever need to boot some other operating system in a computer that has boot problems, there's a good chance you can easily boot it with your Ubuntu USB. 
Just boot Ubuntu in your USB and run 'sudo grub-mkconfig -o /boot/grub/grub.cfg and reboot, or use the USB's GRUB2 in CLI mode, [GRUB2 How To Boot From CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html").

It will take a very long time for your flash memory to wear out, even with a swap area in it, contrary to what you will read posted by all the parrots in many web forums. At lest I haven't worn out any flash memory sticks yet, I imagine it's possible, but hard disks wear out too or have motor or bearing failures, and are more vulnerable to rough handling in general, especially when spinning. :)

---

