---
title: "How to install Ubuntu on an usb stick to get a very fast booting?"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by cyanno on 2010-04-13
Hi, 
since about one month I’m now trying to get acquainted with Linux (Ubuntu). As such I’m a complete greenhorn and of course new in the forum. Therefore first a hello and thanks to everybody because all of you helped me to understand the idea behind Linux!
My problems started with the possible treads during online banking using an OS made by MS.  Knowing Linus is part of a solution I used a program "bankix" based on the 9.04 Kernel. Typically for this Kernel: after installing you have to reboot and hence no possibility to adapt the nvidia driver). And working with an 800x600 solution is catastrophically.

I tried other usb systems; unfortunately they all are very slow for booting (at least what my experience is concerned). So my question: who can give me a hint how to install Ubuntu (ore other Linux systems) on a bootable usb stick which allows a vdery quick and direct booting?

Thanks for any answer!

---

### Post by cyanno on 2010-04-14
Hi, 
since about one month I’m now trying to get acquainted with Linux (Ubuntu). As such I’m a complete greenhorn and of course new in the forum. Therefore first a thanks and hello to everybody because all of you helped me to understand the idea behind Linux!
My problems started with the possible treads during online banking using an OS made by MS.  Knowing Linus is part of a solution I used a program "bankix" based on the 9.04 Kernel. Typically for this Kernel: after installing you have to reboot and hence no possibility to adapt the nvidia driver. And working with an 800x600 solution is catastrophically.

I tried other usb systems; unfortunately they all are very slow at booting (at least what my experience is concerned). So my question: who can give me a hint how to install a quick booting Ubuntu (ore other Linux systems) on a bootable usb stick

Thanks for any answer!

---

### Post by aksx on 2010-04-14
i have install ubuntu on my 8 gb usb stick it runs great and very fast (faster than windows 7). All i did was booted the live CD and while installing ubuntu i chose the usb stick as the destination and selected 'Use The Whole Disk"(or something like that) now it's been running for more than 6 months and i am running out of disk space and thinking of moving ubuntu from the usb stick to the hard disk but still ubuntu runs very fast.:guitar:

---

### Post by ottosykora on 2010-04-14
depends on how fast usb stick you have. Some are 10 times slower then others.

---

### Post by jimmers on 2010-04-17
I have jaunty running on a 16 Gb drive, a Kingston Data Traveller, and it boots faster than my laptop.
I used this tutorial from Ubuntu Geek:-
  	 	 	 	 	 	  
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
[*]The installation will be started now. Just be 	patient, grab a cup of coffee and come back later, your 	installation will be more or less finished by then.  	
[/LIST]

---

### Post by C.S.Cameron on 2010-04-17
NimbleX boots about three times faster than Ubuntu, (in my experience).
But it is not near as polished as Ubuntu.
(It is less than 200MB on thumbdrive).

---

### Post by jimmers on 2010-04-17
Try This:-
  	 	 	 	 	 	  
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

---

### Post by cyanno on 2010-04-17
Thanks for all these comments, especially @Jimmers. I´m not always "online" and sometimes a little bit in lack of time, therefore my late reply.
It seems that Jimmers solution is hitting the point. It is not a question of different kernels or faster USB-Stick. It is just that, when preparing a bootable stick from a live CD you are getting a slow booting with usb. As soon a I have some more time avaible I will try the Jimmers solution and give feedback!
thanks folks
Cyanno

---

### Post by louieb on 2010-04-17
@jimmers Nice USB install instructions - should work well.  

The post install instructions my not be necessary. 1st Ubuntu uses the UUID to identify partitions. -   the old (hd#,#) notation can still be used - the Installer only uses it for other (Windows)  OS

Also Ubuntu v9.10 (Karmic) and the upcoming v10.4 use GRUB2 by default - there is no menu.lst to edit.  grub.conf has replaced it. - to much to go into now but the files you edit are in the /etc directory.

---

### Post by quadproc on 2010-04-17
> **cyanno said:**
> ...

I tried other usb systems; unfortunately they all are very slow for booting (at least what my experience is concerned). So my question: who can give me a hint how to install Ubuntu (ore other Linux systems) on a bootable usb stick which allows a vdery quick and direct booting?
Booting from a USB flash drive will certainly be faster than booting from a CD but it will be quite a bit slower than booting from a normal hard disk so it might not meet your expectations.  However, it is worth trying.

There are several methods of creating a USB boot volume.  Perhaps the simplest is to use the "USB Startup Disk Creator" which is located in System > Administration in Ubuntu Karmic and later releases.

quadproc

---

### Post by cyanno on 2010-04-18
@jimmers
  Now everything is perfect! Your post #4 indeed was the solution of my problems, A lot of thanks for your efforts giving such a detailed info.
   
  Now I´m a little bit embarrassed with my last (and first) 2 postings. When I joined this forum a few days back, I didn´t knew exactly how to look for my postings. So I posted the first one “**How to install Ubuntu on an usb stick to get a very fast booting?” **could´t detect this one in the forum and wrote a new one, this one. And in both postings there are a few interesting comments! e.g. the one of louieb who correctly pointed out that the post install instructions are not at all necessary for Ubuntu 9.10.
   
  Perhaps there is a nice mod who can make one posting out of these both? If not I will send my exuses to louieb and quadproc.
   
  Regards out of Germany 
  Cyanno

---

### Post by jimmers on 2010-04-21
Cyanno,
Glad it worked for you.

---

### Post by acarlstein on 2010-04-28
I created a live usb with Ubuntu 9.10

I am trying to modify the installation menu.

I am compiling different versions of the kernel and I want to have a way to choose them.

update-grub is not working as it should.

Any ideas?

---

### Post by varunendra on 2010-04-28
AFAIK, grub is not installed in live setup. Instead it is isolinux.
Not sure though.

Also, if cyanno (original poster) is concerned with using this usb on different hardware, I think Live Setup is the only way to go.

---

### Post by varunendra on 2010-04-28
To the admins/moderators,

Can you close this thread or merge it with > [http://ubuntuforums.org/showthread.php?t=1454054](http://ubuntuforums.org/showthread.php?t=1454054)with or without the thread starter's permission?

I just learnt that in confusion- he has started another thread (above link) > Now I´m a little bit embarrassed with my last (and first) 2 postings.  When I joined this forum a few days back, I didn´t knew exactly how to  look for my postings. So I posted the first one “**How to install  Ubuntu on an usb stick to get a very fast booting?” **could´t detect  this one in the forum and wrote a new one, this one. And in both  postings there are a few interesting comments! e.g. the one of louieb  who correctly pointed out that the post install instructions are not at  all necessary for Ubuntu 9.10.

So visitors of this thread (like me) would think it an unsolved one and thus drag it to unnecessary length.
Besides, useful comments ought to be placed in right thread. Right?

Just a suggestion.

---

### Post by lisati on 2010-04-28
Threads merged.

---

### Post by varunendra on 2010-04-28
> **lisati said:**
> Threads merged.
Wow! Didn't expect such a blazing fast positive response! This forum never fails to pleasantly surprise me!

---

### Post by lisati on 2010-04-28
> **varunendra said:**
> Wow! Didn't expect such a blazing fast positive response! This forum never fails to pleasantly surprise me!

All part of the service :)

---

