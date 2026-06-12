---
title: "Cannot install on USB drive"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by nonpareilpearl on 2012-10-20
I've been trying to make a USB flash key to boot from as an experiment/something to play with. So far, the experiment has gone poorly. (For the record, I already dual boot Ubuntu and Windows ok, I really just want to be able to this USB thing.)

My issue: I tried following the instructions here on this web page: [http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

Seemed like the most straightforward way to do what I wanted to do. I have the latest LTS ISO (12.04), which is what I'm trying to use. When it starts writing to the USB drive, it stalls at ~5% and throws and error that the volume is no longer present. Basically at this point the USB drive has no partitions/etc., it is just a RAW disk. 

I found these instructions as well: [http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/ubuntu-804-usb-hard-drive-install/)

Which I assume I could use for 12.04, except I'm using a laptop so disconnecting all internal HDDs isn't really possible.

Does anyone have any suggestions? :confused:

---

### Post by offgridguy on 2012-10-20
Glad to see someone being adventures ,  Most of the install problems i read about here
deal with the downloads.  Either onto a USB stick or a disk, when I installed ubuntu I did
it  from  a CD package I purchased on ebay.  I have used it twice now ,on  two different machines, it installs without a hitch {even I can do it  }.  So it seems I have avoided a lot
of install issues by doing this.  Why does it work better?  I dunno.
       
    Why buy something you can download for free??   First it wasn't much  $$ {$ 4.00}
second downloading isn't free.  I pay $39.00 per mo. for 500 mb. {not very much}
every 5oo over costs me around $10.00.  I am always over anyway on my average usage.
Not sure how many mb in a download of ubuntu, but just the updates yesterday were
480 mb.
So for me anyway it is cheaper just to buy the install disk.  :smile:

---

### Post by efflandt on 2012-10-20
Since you apparently mangled your partition(s) on the USB device, the first things you need to do (if you have not yet) is recreate an **msdos partition table** on it and a **FAT32 partition**.  To me that would be most easily done using **gparted** on your working Ubuntu system (install gparted if you do not have it).

Then the easiest way to make your downloaded live/install iso bootable on USB from your working Ubuntu is to use its **Startup Disk Creator**.  If you want and have room for persistent data, there is a slider for that (which ends up being a filesystem within a casper-rw file that ends up loop mounted when booting from the USB).

Note that since the underlying filesystem on the USB is FAT32, that limits the persistent data to around 4 GB max (or available space if less).  Persistent data allows you to save certain settings (timezone, wireless security settings, etc.) and install programs that run after booting.  But initial booting is from a fixed squashfs filesystem, so you cannot update kernel, install other extra video drivers, or anything else that happens during boot before persistent data is mounted.

If you want to do an actual install to USB, (which allows you to update kernels, add video drivers, etc.) you first need the install iso burned to a CD or bootable from different USB device.  Then when you run that and install comes to partitioning, chose **Other**,  set up partition(s) you want on the USB you are doing a full install to, and pay close attention on that screen to put grub in the mbr of the USB device you are installing to (not your internal hard drive).  8 GB minimum is recommended for full install (more is better).

---

### Post by C.S.Cameron on 2012-10-20
Following is step by step for installing 12.04 on a 8GB flash drive on an Intel machine.

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
"Use as:" = "FAT32 file system".
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

### Post by offgridguy on 2012-10-20
>   Following is step by step for installing 12.04 on a 8GB flash drive on an Intel machine.

Thank you for this I'm definitely going to save it.

---

### Post by nonpareilpearl on 2012-10-20
> **C.S.Cameron said:**
> Following is step by step for installing 12.04 on a 8GB flash drive on an Intel machine.

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
...

Thank you for the detailed instructions, but unfortunately like I mentioned I'm using a laptop so I cannot access the HDD so easily.

> **efflandt said:**
> Since you apparently mangled your partition(s) on the USB device, the first things you need to do (if you have not yet) is recreate an msdos partition table on it and a FAT32 partition. To me that would be most easily done using gparted on your working Ubuntu system (install gparted if you do not have it).

I actually did this a couple times. Unfortunately, I still ran into the same problem at the same spot :(

---

### Post by C.S.Cameron on 2012-10-20
You do not need to disconnect the hard drive if you are careful of what disk you install to and where you put the bootloader, (grub), as mentioned at the bottom of the above.

---

### Post by nonpareilpearl on 2012-10-21
> **C.S.Cameron said:**
> You do not need to disconnect the hard drive if you are careful of what disk you install to and where you put the bootloader, (grub), as mentioned at the bottom of the above.

Sorry I missed that! I'll give it a try - thank you!

---

