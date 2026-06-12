---
title: "Install to USB &gt; Not LIVE"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by groveborn on 2010-03-20
I'm just wondering if the method for installing to a regular drive would work for a flash drive, and still be portable?  I know I could use a live usb, but I want a real installation for diagnostics and such (and just to have it).  I need to be able to use Wine, as some of the utilities and programs I want to use are Windows only.

I know I can just install it on the flash drive, but I just don't know if it'll work on other computers.  Obviously I would be using the x86 install, not the AMD64 for maximum compatibility, and I would use 9.10 for now.

---

### Post by Ozymandias_117 on 2010-03-20
System -> Administration -> USB Startup Disk Creator make sure you select "When starting up from this disk documents and settings will be:" "Stored in Reserved Extra Space" and move the slider bar to the max.

---

### Post by jimmers on 2010-03-20
Try this tutorial from some-one who's name I forget.

  	 	 	 	 	 	  **[SIZE=4]How-to: Installing Ubuntu Linux on a usb pendrive[/SIZE]**

 This tutorial will show how-to install Ubuntu on a usb stick. Even though this tutorial uses Ubuntu as its base distribution, you could virtually use any type of Linux liveCD distribution.
 Being able to run Linux out of a usb bar is a great way to enjoy the live CD experience (being able to use Linux on any computer you might get by) and the big advantage of being easier to carry around than a CD.
 **[SIZE=4]1. Requirements[/SIZE]**

 In order to reproduce this tutorial, you will need a few items such as:  
 
[LIST]
[*]a ubuntu liveCD  	
[*]a usb bar of at 	least 1G  	
[*]a running Linux operating system  	
[/LIST]
 Now that you have all this, it is time to prepare you USB bar do host the Ubuntu liveCD files.
 **[SIZE=4]2. Setting up the USB disk[/SIZE]**

 **[SIZE=3]2.1. Finding the device[/SIZE]**

 In the first place, you need to plug your usb drive and check under which device it is associated. To find out the device, run:  
 $ sudo fdisk -l
 On my system, the device appears as being */dev/sdb*, I will therefore use /dev/sdb as a reference for this tutorial, please replace it accordingly to your system (might be sda, sdc ...).
Once you found your device, you are going to create the partitions.  
 Using the wrong device name might destroy your system partition, please double check
 **[SIZE=3]2.2. Making the partitions[/SIZE]**

 Make sure every of your already mounted partition are unmounted:
 $sudo umount /dev/sdb1
 and then launch **fdisk**, a tool to edit partition under linux:
 sudo fdisk /dev/sdb
 We are going delete all the partition and then create 2 new partition: one fat partition of 750M which will host the files from the live CD iso, and the rest on another partition.
 At fdisk prompt type *d x* where x is the partition number (you can simply type d if you only have one partition), then:
 
[LIST]
[*]*n* to 	create a new partition  	
[*]*p* to make 	it primary  	
[*]*1* so it 	is the first primary partition  	
[*]Accept the default 	or type *1* to start from the first cylinder  	
[*]*+750M* to 	make it 750 Meg big  	
[*]*a* to 	toggle the partition active for boot  	
[*]*1* to 	choose the 1 partition  	
[*]*t* to 	change the partition type  	
[*]*6* to set it to FAT16  	
[/LIST]
 Now we have out first partition set up, let's create the second one:
 
[LIST]
[*]*n* to 	create yet again a new partition  	
[*]*p* to make 	it primary  	
[*]*2* to be 	the second partition  	
[*]Accept the default 	by typing Enter  	
[*]Accept the default 	to make your partition as big as possible  	
[*]Finally, type *w* to write the change 	to your usb pendrive  	
[/LIST]
 Partitions are now created, let's format them.
 **[SIZE=3]2.3. Formatting the partitions[/SIZE]**

 The first partition is going to be formated as a FAT filesystem of size 16 and we are going to attribute it the label "liveusb".
 $ sudo mkfs.vfat -F 16 -n liveusb /dev/sdb1
 The second partition is going to be of type ext2 with a blocksize of 4096 bytes and the label **casper-rw**. Mind that it has to be labeled as *casper-rw* otherwise the tutorial won't work!.
 $ sudo mkfs.ext2 -b 4096 -L casper-rw /dev/sdb2
 At this stage, our usb pendrive is ready to host the liveCD image. Now, let's copy the files to the usb bar.
 


 **[SIZE=4]How-to: Installing Ubuntu Linux on a usb pendrive -- page 2[/SIZE]**

 **[SIZE=4]3. Installing Ubuntu on the USB stick[/SIZE]**

 **3.1. Mounting Ubuntu liveCd image**

 In the first place we need to mount our ubuntu iso. Depending if you have the .iso file or the CD, there is 2 different ways of mounting it.
 **3.1.1. Mounting from the CD**

 People using Ubuntu or any other user-friendly distro, might just have to insert the cd and it will be mounted automatically. If this is not the case:
 $ sudo mount /media/cdrom
 should mount it.
 **3.1.2. Mounting from an .iso image file**

 We will need to create a temporary directory, let say */tmp/ubuntu-livecd* and then mount our iso (I will be using a feisty fawn iso).
 $ mkdir /tmp/ubuntu-livecd
$ sudo mount -o loop /path/to/feisty-desktop-i386.iso /tmp/ubuntu-livecd
 Once the cd image is ready, it is time to mount the newly created usb bar partitions:
 **3.2. Mounting the usb bar partitions**

 Same here, you might be able to get both your partition by simply replugging the usb pendrive, partition might appears as: */media/liveusb* and */media/casper-rw*. If this is not the case, then you will need to mount them manually:
 $ mkdir /tmp/liveusb
$ sudo mount /dev/sdb1 /tmp/liveusb  
 All the partitions we need are now mounted, let's copy the files.
 **3.3. Copying the files to the usb bar**

 Let positionned yourself on the CD image directory (in my case: /tmp/ubuntu-livecd , but it might be /media/cdrom , and copy at the root of your usb first partition:
 
[LIST]
[*]the directories: 	'casper', 'disctree', 'dists', 'install', 'pics', 'pool', 'preseed', 	'.disk'  	
[*]The content of 	directory 'isolinux'  	
[*]and files 	'md5sum.txt', 'README.diskdefines', 'ubuntu.ico'  	
[*]as well as files: 'casper/vmlinuz', 	'casper/initrd.gz' and 'install/mt86plus'  	
[/LIST]
 $ cd /tmp/ubuntu-livecd
$ sudo cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz casper/initrd.gz install/mt86plus /tmp/liveusb/
 It might complain about symbolic links not being able to create, you can ignore this.
 Now let's go to the first partition of your usb disk and rename *isolinux.cfg* to *syslinux.cfg*:
 $ cd /tmp/liveusb
$ sudo mv isolinux.cfg syslinux.cfg
 change /tmp/liveusb according to your settings
 Edit syslinux.cfg so it looks like:
 DEFAULT persistent GFXBOOT bootlogo GFXBOOT-BACKGROUND 0xB6875A APPEND  file=preseed/ubuntu.seed boot=casper initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- LABEL persistent   menu label ^Start Ubuntu in persistent mode   kernel vmlinuz   append  file=preseed/ubuntu.seed boot=casper persistent initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- LABEL live   menu label ^Start or install Ubuntu   kernel vmlinuz   append  file=preseed/ubuntu.seed boot=casper initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- LABEL xforcevesa   menu label Start Ubuntu in safe ^graphics mode   kernel vmlinuz   append  file=preseed/ubuntu.seed boot=casper xforcevesa initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- LABEL check   menu label ^Check CD for defects   kernel vmlinuz   append  boot=casper integrity-check initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- LABEL memtest   menu label ^Memory test   kernel mt86plus   append - LABEL hd   menu label ^Boot from first hard disk   localboot 0x80   append - DISPLAY isolinux.txt TIMEOUT 300 PROMPT 1 F1 f1.txt F2 f2.txt F3 f3.txt F4 f4.txt F5 f5.txt F6 f6.txt F7 f7.txt F8 f8.txt F9 f9.txt F0 f10.txt Woof, finally we have our usb disk almost usuable. We have a last thing to do: make the usb bootable.
 **3.4. Making the usb bar bootable.**

 in order to make our usb disk bootable, we need to install *syslinux* and *mtools*:
 $ sudo apt-get install syslinux mtools
 And finally unmount /dev/sdb1 and make it bootable:
 $ cd
$ sudo umount /tmp/liveusb
$ sudo syslinux -f /dev/sdb1  
 Here we are :D , reboot, set your BIOS to boot from the usb bar and enjoy Ubuntu linux from a pendrive
 **4. Troubleshooting**

 If you are having trouble booting on the usb bar, this might be due to your MBR being corrupted. In order to fix it up, you can use lilo (I installed lilo on my box only for thid purpose).
 $ lilo -M /dev/sdb
 will fix the MBR on device /dev/sdb


Hope it helps, best of luck.

---

### Post by efflandt on 2010-03-20
You can do a regular Ubuntu install to USB flash or hard drive.  Just make absolutely certain that you pay attention to the **Advanced** button at the summary screen after setting partitions just before installation proceeds, to put grub on the mbr of the USB drive (instead of default to your main hard drive).

Since Ubuntu uses UUID to identify partitions in fstab, that should work on any computer (it works as well whether it ends up as sdb on my laptop or sdf on my desktop).  If you activate certain drivers for certain computers, that should work automatically too, as long as you do not need mutually exclusive drivers.  For example I have Broadcom STA activated, which is ignored on a laptop with wireless supported by default modules, and used automatically on another laptop with BC4311 or BCM4312.  However, if you activate Broadcom B43 for a different type, it deactivates Broadcom STA.

Note that Mint8 based on Ubuntu apparently has UUID disabled by default, so unless you enable that, it may not boot if it ends up as a different drive on a different computer.

If you take a tip from live iso on USB, you may want to use tmpfs for /tmp in /etc/fstab:
tmpfs /tmp tmpfs nosuid,nodev 0 0

8 GB is minimum recommended for full install.  It will work on 4 GB, but that does not leave much room for extras that you apparently want to add.

---

### Post by Herman on 2010-03-20
+1 +1

I agree with both Ozymandias_117 because the USB startup disk creator is the quickest and easiest way to make a 'persistence' type of installation. There's no need to go through a long and complicated series of manual procedures using the terminal nowadays.
The USB startup disk is most useful when you want to have a USB that you can use for installing Ubuntu with because it works as a live CD, and features the Ubuntu installer.

I agree with and efflandt because the normal Ubuntu installed in a USB is more useful as a utility disk because it boots with GRUB, so you can use it to boot an operating system in a computer that has boot problems. 
Since Ubuntu Hardy Heron came out the normal operating system seems to be able to detect hardware and set up networking and the xserver automatically on boot-up for most computers just as well as a live CD can.
Another advantage of the regular installation in a USB is that you will have the same file paths and file names as everybody else and you can follow how-tos  in Ubuntu Web Forums. The [Tutorials & Tips]("http://ubuntuforums.org/forumdisplay.php?f=100") section of the Ubuntu Web Forums can help you do all kinds of things with Ubuntu when you have a regular installation. :D

---

