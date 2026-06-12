---
title: "Pendrive linux"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by Uriziel on 2010-04-24
I'd like to install linux on a pendrive. I have tried DSM before, but did't like it at all. What I'm looking for is ability to write data on this pendrive (as far as I noticed dsm didn't allow me to do that) and video hardware acceleration. Didn't try Ubuntu, but I'd prefer something else. 
Thanks in advance
Uriziel.

---

### Post by Dayofswords on 2010-04-24
theres... pendrive linux

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by Uriziel on 2010-04-24
Ofcourse, i found it before, but it didn't explain things which I asked about.

---

### Post by FrPaulB on 2010-04-24
You could try Puppy Linux. Download the .iso and then run Puppy, either by burning to a CD or using unetbootin to make a USB stick. Run it using the mode puppy pfix=ram and then use the built in tools to do a "frugal" install to a USB stick. It should be fine with a 1Gb stick (my installation is on a 2GB stick because that's what I had spare). Puppy saves all your stuff in a "pupsave file" which you can store on the same stick. Try [www.puppylinux.org]("http://www.puppylinux.org") as a start point. There is a forum with plenty of help at [http://murga-linux.com/puppy/ ]("http://murga-linux.com/puppy/")

---

### Post by viralmeme on 2010-04-24
> **Uriziel said:**
> I'd like to install linux on a pendrive. I have tried DSM before, but did't like it at all. What I'm looking for is ability to write data on this pendrive ..

Download the latest Lubuntu ISO and save somewhere.

Boot up your current Ubuntu system and select USB startup disk creator and select the ISO you just downloaded.

Allow it to select the whole of the USB device and install, then delete the casper-rw file.

Fireup *GParted* and resize the partition to about 768MB. Then create a new ext2 partition in the free space and label this casper-rw.

Boot from the USB and it'll save any new changes to the casper-rw partition.

You'll need a 4GB device to be usable.

/dev/sdb1             768M  398M  370M  52% /cdrom
/dev/sdb2             3.1G  522M  2.4G  18% /media/casper-rw

---

### Post by jimmers on 2010-04-24
Try this tutorial from Ubuntu-Geek:-
  	 	 	 	 	 	   was reading [How to install Ubuntu Linux from USB Stick]("http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html") posted on this site a while ago, and found it to be quite some work to get Ubuntu working on a USB stick. Besides, having to prepare your USB device, creating a separate partition on it which will be more or less “useless” after the installation, giving up 750MB of space?  
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
Depending on your Dist. you may not need part 2,


It works for me,


Good Luck

---

### Post by 2hot6ft2 on 2010-04-24
> **jimmers said:**
> 
**open menu.lst** with 	vi (make a backup first!)  	

There is no menu.lst in 9.10 or newer (unless you use the server install disc from what I've read). I'm not sure about 9.04 since I skipped that release.

And with both the usb flash and the livecd in it would depend on the settings in the BIOS for boot priority as to which one it would actually boot.

Nice guide just the same.

I removed the hard drive when I did my usb install so the usb's grub wouldn't show the hard drives installs and it wouldn't be able to make any changes to my hard drive at all. That way it was more universal as far as being able to use it in other machines.

---

### Post by Dayofswords on 2010-04-24
> **2hot6ft2 said:**
> There is no menu.lst in 9.10 or newer (unless you use the server install disc from what I've read). I'm not sure about 9.04 since I skipped that release.


its in 9.04 :)

---

### Post by C.S.Cameron on 2010-04-24
Using usb-creatoor as mentioned in reply 5 is probably the easiest and fastest method of creating a persistent flashdrive as long as you don't need to save more than 4GB of stuff, as that's the maximum size of the persistence file.

---

### Post by Uriziel on 2010-04-25
I'd like to isntall some additional soft, how can i do that? I mean, repository ones

---

### Post by C.S.Cameron on 2010-04-25
That is the point of the usb-creator persistent install.
You can install whatever additional software you want as long as it not larger than 4GB, of course your thumbdrive needs to be large enough.

Of course you can just install to thumbdrive like to internal drive,similar to the Jimmers 1-13, I would suggest unplugging he internal hard drive first though.

---

### Post by viralmeme on 2010-04-26
> **Uriziel said:**
> I'd like to isntall some additional soft, how can i do that? I mean, repository ones
Enable the repositories and then use Synaptic or apt-get ..

---

### Post by acarlstein on 2010-04-28
How about changing the installation menu?

I created a live USB that allowed to store changes but I can't manage to change the installation menu.

Not even update-grub seems to do the magic.

Why do I want to do that?
I am compiling different version of kernels in it but I can't make the installation menu to give me the option to use them.

---

### Post by Atreus10 on 2010-04-28
I suggest [virtualbox]("http://www.virtualbox.org/").  it's a nice, free program that lets you have persistance.  create a virtualbox fixed-size virtual hard drive and copy it to the pen drive.  might want to copy the vbox installer to the drive too, but that's not necessary... you have to install vbox on every computer you use it on, though.  i use it at my college, whose computers reset after every logoff so it's no big deal if i install stuff.  as for the OS, i'd suggest [SliTaz]("http://www.slitaz.org/en/") for anything512mb to  2 gigs and... iunno, puppy dog for 4-8 gigs, any normal distro for 8+ gig drive.
acceleration is difficult, though.  you might be able to get it with a bigger distro, though.  vbox has options for it.
the virtualbox guest additions are really nice, but they are rarely able to be use on specialized small linux distros (slitaz is a good example.  it uses it own repositories if i recall correctly, so getting the packages needed to install the guest additions is a mite difficult.)

anyways, that's my two cents.  ignore me if ya want.

---

### Post by acarlstein on 2010-06-17
Atreus10, I think your idea is fantastic;however, it is not what I am searching for.

The only big problem of your solution is the following: Speed.
It is already having a toll to work using the pendrive as a HD. If you add the speed you would use using virtual box it would be even slower. 

I was thinking to see how to modify the initrd, perhaps that would do the magic. For what I saw so far, the image is loaded on memory and then it points to the USB as the hd. You can save files, etc but you can't modify other things. In this case, you can't modify the menu.

Thanks anyways for your feedback

---

### Post by emarkay on 2010-06-18
Big apologies for "hijacking" this thread, but has anyone got a Persistent Lucid USB updated to the latest (2.6.32-23-generic) Kernel and have it successfully boot ?
See issue (and assist) here: [http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)
Thanks!

---

