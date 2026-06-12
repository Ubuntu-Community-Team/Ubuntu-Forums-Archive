---
title: "Install ubuntu ON usb"
date: 2013-03-22
forum: Installation &amp; Upgrades
---

### Post by ashu1234 on 2013-03-22
For portability of my files and settings, is it possible to install ubuntu ON usb...
I have tried Yumi, Multiboot installer, Sardu as directed on many sites, but what it does it loading ubuntu live desktop from USB. In this case each and every file/software and setting is saved in RAM (i guess) instead of USB. I want those files to be placed on USB, just like it happens on harddisk.

Similar to what happens in puppy linux, however its too complicated to install all the dependency and software in that linux.

---

### Post by darkod on 2013-03-22
Yes, but you will have to boot the installer from a cd or another usb. Use the manual install method and simply select the usb you want as destination. Make the partitions you want, make sure you install the bootloader on the usb too, not the int hdd.

That's it.

---

### Post by sanderj on 2013-03-22
> **ashu1234 said:**
> For portability of my files and settings, is it possible to install ubuntu ON usb...
I have tried Yumi, Multiboot installer, Sardu as directed on many sites, but what it does it loading ubuntu live desktop from USB. In this case each and every file/software and setting is saved in RAM (i guess) instead of USB. I want those files to be placed on USB, just like it happens on harddisk.

Similar to what happens in puppy linux, however its too complicated to install all the dependency and software in that linux.

Maybe I misunderstand, but you want can be done with the persistent USB key option in Ubuntu. Boot Ubuntu from CD, put in a 4GB USB stick, start "usb-creator-gtk" and follow the guide.

HTH

---

### Post by C.S.Cameron on 2013-03-22
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
(Optional home partition).

(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.

(Optional swap space, allows hibernation)
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

### Post by ashu1234 on 2013-03-23
> **darkod said:**
> Yes, but you will have to boot the installer from a cd or another usb. Use the manual install method and simply select the usb you want as destination. Make the partitions you want, make sure you install the bootloader on the usb too, not the int hdd.

That's it.

I tried it, but system hanged during ubuntu installation. Maybe, because i am using virtualbox because i am newbie and dont want to messup with the grub on HDD. I will try direct installation now.

In btw, I will also try usb gtk creator today...

Thanks for your quick reply...

---

### Post by ashu1234 on 2013-03-23
> **sanderj said:**
> Maybe I misunderstand, but you want can be done with the persistent USB key option in Ubuntu. Boot Ubuntu from CD, put in a 4GB USB stick, start "usb-creator-gtk" and follow the guide.

HTH

Will startup disk also allows installing of software besides saving my files...

---

### Post by ManamiVixen on 2013-03-23
Yes, it could. I did it before but it might make the system unstable.

---

### Post by darkod on 2013-03-23
You never mentioned VBox. I don't see how VBox could help you. You only need to boot your computer from a cd or usb stick prepared with ubuntu, and install onto the destination usb stick.

If you feel more comfortable, disconnect your hdd when doing this, you want to install onto a usb stick anyway.

VBox might not support your usb ports the way you think by default, you might need to install additions and play around with options. I don't see how it can help.

Yes, a live usb with persistance can keep data after poweroff, but your idea to install onto a usb is better. I would try that first.

---

### Post by ashu1234 on 2013-03-24
> **darkod said:**
> You never mentioned VBox. I don't see how VBox could help you. You only need to boot your computer from a cd or usb stick prepared with ubuntu, and install onto the destination usb stick.

If you feel more comfortable, disconnect your hdd when doing this, you want to install onto a usb stick anyway.

VBox might not support your usb ports the way you think by default, you might need to install additions and play around with options. I don't see how it can help.



Removing and adding hdd is a matter of click in vbox than physcally removing the cables. So i used vbox... Plus it assured actual system will go no harm.
Now, i have physically removed hdd and installed ubuntu on pendrive, its working perfectly. Thanks everyone...

Now just want to ask, if steps for Lubuntu will be same???
Although major systems are average, few systems have very low specifications, processor is sufficient (around 2.4 GHz) however RAM is just 256MB.
Also suggest, if any aliter is present besides Lubuntu, if Lubuntu too will not work, with same install on usb feature.

---

### Post by ashu1234 on 2013-03-24
Thanks C.S. Cameron, your steps, made it very easy to partition the usb drive according to my needs.

---

### Post by C.S.Cameron on 2013-03-24
> **ashu1234 said:**
> Removing and adding hdd is a matter of click in vbox than physcally removing the cables. So i used vbox... Plus it assured actual system will go no harm.
Now, i have physically removed hdd and installed ubuntu on pendrive, its working perfectly. Thanks everyone...

Now just want to ask, if steps for Lubuntu will be same???
Although major systems are average, few systems have very low specifications, processor is sufficient (around 2.4 GHz) however RAM is just 256MB.
Also suggest, if any aliter is present besides Lubuntu, if Lubuntu too will not work, with same install on usb feature.

Lubuntu install should work the same.

---

### Post by xXSanitariumXx on 2013-03-28
> **sanderj said:**
> Maybe I misunderstand, but you want can be done with the persistent USB key option in Ubuntu. Boot Ubuntu from CD, put in a 4GB USB stick, start "usb-creator-gtk" and follow the guide.

HTH

I have trying to do this for the longest times but it seams no matter what brand or size I use I get errors in the middle of the process that say that the operation failed. I even bought a 16GB USB 3.0 drive just for Ubuntu which does the same thing. The only version of Ubuntu that will install properly is 7.04, anything after that gets the same errors. Its quite annoying too! I also hate that Ubuntus tool will not allow more then 4GBs of space to a USB device because thats alot of space wasted being I got the 16GBs just for Ubuntu. I run Windows 7 on one which does great for a portalable drive to be used for web surfing. I would rather have the full use of the whole USB drive for Ubuntu then 4GB, then again if I could even get it to work it would be nice. I wonder what is different from 7.04 up to the current versions that they wont complete, but 7.04 will.

---

### Post by C.S.Cameron on 2013-04-02
> **xXSanitariumXx said:**
> I have trying to do this for the longest times but it seams no matter what brand or size I use I get errors in the middle of the process that say that the operation failed. I even bought a 16GB USB 3.0 drive just for Ubuntu which does the same thing. The only version of Ubuntu that will install properly is 7.04, anything after that gets the same errors. Its quite annoying too! I also hate that Ubuntus tool will not allow more then 4GBs of space to a USB device because thats alot of space wasted being I got the 16GBs just for Ubuntu. I run Windows 7 on one which does great for a portalable drive to be used for web surfing. I would rather have the full use of the whole USB drive for Ubuntu then 4GB, then again if I could even get it to work it would be nice. I wonder what is different from 7.04 up to the current versions that they wont complete, but 7.04 will.


For what it is worth the following is how I make a flash drive with more than 4GB persistence:

Boot Live CD or Live USB.
Plug in flash drive.
Start gparted.

Create 2 GB FAT32 partition, (on the left side of the bar). (size is optional, extra space can be used for file storage and transfer to Windows machines).

Create a 4 GB ext2 partition to the right of this, labeled it "casper-rw". (ext3 and ext4 also work).

Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition).

Close gparted.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, Go to the root folder of your Live USB
    Enter the syslinux directory, (or for UNetbootin the root directory).
    Make the syslinux.cfg file writeable
    Replace the contents of the file syslinux.cfg with:

```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD, reboot.


First time booting go to users and groups and create an account with yourself up as an Administrator, with password if desired.

Note:
The above code will bypass the Try/Install and Language screens.

---

