---
title: "Trying to create Lucid usb startup"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zenlunatic on 2010-04-09
[[IMG]http://img130.imageshack.us/img130/2857/usbn.th.png[/IMG]](http://img130.imageshack.us/i/usbn.png/)

I cannot create a usb startup disk.  I've a 2G drive.  As you can see in the image, I have little caution symbols next to two /dev/sdb /dev/sdb1. sdb1 says not enough space, and sdb says needs to be formatted.  I've hit format with each highlighted and I am still not able to move past these two error messages.  I even used gparted to format outside the usb-creator-gtk application.  The drive is not U3, its a verbatim brand.

Here is my $mount output.

```
justin@mini:~/Desktop$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/justin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=justin)
192.168.1.199:/nfs on /mnt/nfs type nfs (rw,remount,addr=192.168.1.199)

```

---

### Post by zenlunatic on 2010-04-09
bump

---

### Post by jimmers on 2010-04-10
Try this tutorial by Ubuntu Geek:-
  	 	 	 	 	 	  
I was reading [COLOR=#000080]_[How to install Ubuntu Linux from USB Stick]("http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html")_[/COLOR] posted on this site a while ago, and found it to be quite some work to get Ubuntu working on a USB stick. Besides, having to prepare your USB device, creating a separate partition on it which will be more or less “useless” after the installation, giving up 750MB of space? 
There had to be a better way.
Together with a colleague of mine, I decided to figure out whether there could be an easier way to install Ubuntu on a USB device.
I found a way of doing it in a much simpler way… without creating the separate partition to store the LiveCD:
A couple of assumptions to take into account when going through this manual:
 
[LIST]
[*]My computer (Dell 	D820 [COLOR=#000080]_[laptop]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html")_[/COLOR]) 	has 1 internal disk, devided into 3 partitions (dell utility - 	windows - Ubuntu 8.04)  	
[*]Just one USB 	device (in my case a 250GB harddisk  	
[*]BIOS configured to enable boot from internal 	HDD, CD/DVD and USB [COLOR=#000080]_[Storage 	device]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html")_[/COLOR]  	
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
[*]If there is 	anything to migrate from other installations on your [COLOR=#000080]_[computer]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html")_[/COLOR] 	(most likely not), do whatever you want, and click Forward;  	
[*]**The next screen 	is important** - It is titled: “Ready to Install”. **Be 	careful here: before clicking on Forward, **make sure you [B]click 	on the “Advanced” Button!
[/B]This will open a new screen, 	giving you the option whether and where to install the bootloader. 	**Select your USB device** (in my case it was /dev/sdb) to 	install the bootloader to;
Exit this screen and click on Forward 	in the “Ready to Install” screen, which will be shown;  	
[*]The installation will be started now. Just be 	patient, grab a cup of coffee and come back 15 minutes later, your 	installation will be more or less finished by then.  	
[/LIST]
 So you have finished the installation. However, when you will be restarting your system from USB, you will find out that the partition you just installed Ubuntu to cannot be mounted.
Here comes the trick:
 
[LIST=1]
[*]Once the 	installation is finished, reboot your [COLOR=#000080]_[PC]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html")_[/COLOR] 	(this is the safest) from your LiveCD, with your USB device 	connected;  	
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
 Works for me on my Kingston data Traveller 16 Gb drive.
 


 Worth a try, good luck

---

### Post by penguin386 on 2010-04-10
It didn't work for me either.  My Dell Mini 9 boots from the USB drive, but I just get a blank screen with the mouse cursor in the shape of a clock.  So far, Jolicloud is the only Linux distro that boots from a flash drive with no hassle on my Dell Mini 9.  Jolicloud even recognizes my wireless adapter and sees my home wireless access point with no hassle.  Why can't Ubuntu do that?

---

