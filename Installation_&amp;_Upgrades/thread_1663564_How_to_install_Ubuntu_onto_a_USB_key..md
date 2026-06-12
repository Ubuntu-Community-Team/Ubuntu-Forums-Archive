---
title: "How to install Ubuntu onto a USB key."
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by Howlin1 on 2011-01-09
Hello. I am a noob at Linux and I would like to know how to install Ubuntu onto an 8gb USB key. I have version 10.10 of Ubuntu. Is there anything I should/shouldn't do?

---

### Post by mlamorey on 2011-01-09
I have not done this, but I just installed 9.04 and then 10.04 on two different laptops. What you ask, should be simple.
Get or make a 10.10 CD
Boot from the 10.10 CD 
     - this may require pushing delete or F2 during boot up to get into your bios and rearranging the device boot priorities to move the CD in front of the HDD. While there you might want to put the USB devices in front of the HDD also.
Once you boot from the Ubuntu CD it should be an option to install it to a USB device. Along with other options like boot from the CD, install to the HDD etc.

Hope this helps
Cheers,

---

### Post by wilee-nilee on 2011-01-09
> **Howlin1 said:**
> Hello. I am a noob at Linux and I would like to know how to install Ubuntu onto an 8gb USB key. I have version 10.10 of Ubuntu. Is there anything I should/shouldn't do?

Are you familiar with installing Ubuntu and the grub bootloader?

---

### Post by Howlin1 on 2011-01-09
No sorry I don't know anything about  installing Ubuntu and grub bootloader. 
At the moment I have it on a 2gb USB key. I only put it on that (I didn't install it) to see how it was.

---

### Post by wilee-nilee on 2011-01-09
> **Howlin1 said:**
> No sorry I don't know anything about  installing Ubuntu and grub bootloader. 
At the moment I have it on a 2gb USB key. I only put it on that (I didn't install it) to see how it was.

Thanks for the response, so you can do a full install onto the 8gig thumb. You would preformat it with gparted in the Ubuntu live session to a ext4 partition. You would close gparted then hit the install button, when you get to the partitioning area of the install you would choose a custom install. Here you would look at the grub line and make sure it was installed to the thumbs master boot record=mbr which would be the drive letter without the partition number. For example if the partition you made was sdb1, the mbr is sdb. So then you would click on the box next to the thumb and in the popup choose ext4, and put tis in the box below / this is the root mount point, click the format box, and close the popup hit install, and follow the directions in setting the time zone and a user name and password.

Make sure you know how gparted was identifying the thumb eg sda or sdb or sdc etc.

---

### Post by wilee-nilee on 2011-01-09
I think it might be helpful here to as well to identify the computer operating systems and if you have a recovery disc or a install disc if it XP before proceeding as well.

---

### Post by Howlin1 on 2011-01-09
> **wilee-nilee said:**
> Thanks for the response, so you can do a full install onto the 8gig thumb. You would preformat it with gparted in the Ubuntu live session to a ext4 partition. You would close gparted then hit the install button, when you get to the partitioning area of the install you would choose a custom install. Here you would look at the grub line and make sure it was installed to the thumbs master boot record=mbr which would be the drive letter without the partition number. For example if the partition you made was sdb1, the mbr is sdb. So then you would click on the box next to the thumb and in the popup choose ext4, and put tis in the box below / this is the root mount point, click the format box, and close the popup hit install, and follow the directions in setting the time zone and a user name and password.

Make sure you know how gparted was identifying the thumb eg sda or sdb or sdc etc.
I am sorry, but I have no idea what sda or sdb or sdc, ext4 or mbr means.

---

### Post by VonFilmjölk on 2011-01-09
Don't forgett that if you install or upgrade any windows version, while having Ubuntu installed.
It will mess up your grub loader, and u will have to re install the grub loader using a LiveCD. 

even a windows recovery partition can do this if your unlucky.
I have also heard rumors of some people installing ubuntu onto usbdrives and then not being able to load the grub without the usb drive.

---

### Post by wilee-nilee on 2011-01-09
> **Howlin1 said:**
> I am sorry, but I have no idea what sda or sdb or sdc, ext4 or mbr means.

Well boot the 2 gig thumb and look at the hard drive with the gparted partitioner that might get you orientated.

---

### Post by wilee-nilee on 2011-01-09
> **VonFilmjölk said:**
> Don't forgett that if you install or upgrade any windows version, while having Ubuntu installed.
It will mess up your grub loader, and u will have to re install the grub loader using a LiveCD. 

even a windows recovery partition can do this if your unlucky.
I have also heard rumors of some people installing ubuntu onto usbdrives and then not being able to load the grub without the usb drive.

Please read the thread before posting this is a install to a thumb.:)

I instructed the user how to avoid putting grub into the computers mbr.

---

### Post by VonFilmjölk on 2011-01-09
Sda is a partition for example if u only have one HD but two partitions on it  they will be displayed as Sda1 , Sda2
if u know the size of your partitions u can easily identify them, Ext4 stands for fourth extended filesystem. not sure but i think it is linux version of NTFS of FAT.

---

### Post by VonFilmjölk on 2011-01-09
> **wilee-nilee said:**
> Please read the thread before posting this is a install to a thumb.:)

I instructed the user how to avoid putting grub into the computers mbr.
my apologies sir,

---

### Post by C.S.Cameron on 2011-01-09
Try a persistent install it's quick and easy using either Startup Disk Creator from the live CD or Universal from PendriveLinux .com

---

### Post by wilee-nilee on 2011-01-09
> **VonFilmjölk said:**
> Sda is a partition for example if u only have one HD but two partitions on it  they will be displayed as Sda1 , Sda2
if u know the size of your partitions u can easily identify them, Ext4 stands for fourth extended filesystem. not sure but i think it is linux version of NTFS of FAT.

sda or sdb or sdb is the disc identifier as a whole and the master boot record as well.

This is a user that is having a hard time understanding some basic stuff. Let me ask are you helping here? I like to share but your not really being accurate or helping in my honest opinion.:)

---

### Post by Howlin1 on 2011-01-09
> **wilee-nilee said:**
> Well boot the 2 gig thumb and look at the hard drive with the gparted partitioner that might get you orientated.
Could I just try and install Ubunut onto the 8gb by simply installing it and follow the instructions it give?

---

### Post by C.S.Cameron on 2011-01-09
Following step by step for Full install of 10.10 to USB device, adjust partition size to suit:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by wilee-nilee on 2011-01-09
OP can you follow C.S.Cameron's advice?

---

### Post by Howlin1 on 2011-01-09
> **wilee-nilee said:**
> OP can you follow C.S.Cameron's advice?
Yea I can understand it thanks. I will try it tomorrow and report back here. Thanks :)

---

### Post by wilee-nilee on 2011-01-09
> **Howlin1 said:**
> Yea I can understand it thanks. I will try it tomorrow and report back here. Thanks :)

Cool, we do things a little differently, but if I needed, help they would be who I was looking for.:)

---

### Post by Howlin1 on 2011-01-10
> **wilee-nilee said:**
> Cool, we do things a little differently, but if I needed, help they would be who I was looking for.:)
I have managed to install Ubunut onto my USB key (I'm on it at the moment). I have a problem with the update manager though. When I go to try install the updates is tells me 
"The upgrade needs a total of 505M free space on disk '/'. Please free at least an additional 252M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

How can I get more space on that or should I even attempt it?

---

### Post by wilee-nilee on 2011-01-10
> **Howlin1 said:**
> I have managed to install Ubunut onto my USB key (I'm on it at the moment). I have a problem with the update manager though. When I go to try install the updates is tells me 
"The upgrade needs a total of 505M free space on disk '/'. Please free at least an additional 252M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

How can I get more space on that or should I even attempt it?

I didn't see both posts by C.S.Cameron, I thought you were going to do a full install per post 16. A ISO loaded with a persistence is okay, but has some limitations. Can you post a screen shot of gparted looking at the thumb.

If you want a full install then that is what you should do it sounds like that is not what you have done.

---

### Post by Howlin1 on 2011-01-10
> **wilee-nilee said:**
> I didn't see both posts by C.S.Cameron, I thought you were going to do a full install per post 16. A ISO loaded with a persistence is okay, but has some limitations. Can you post a screen shot of gparted looking at the thumb.

If you want a full install then that is what you should do it sounds like that is not what you have done.
I did follow the instructions as per post 16.

I'm sorry but I don't know where to find the gparted thing.

---

### Post by wilee-nilee on 2011-01-10
n

---

### Post by C.S.Cameron on 2011-01-11
> **Howlin1 said:**
> I did follow the instructions as per post 16.

I'm sorry but I don't know where to find the gparted thing.


Try running Computer Janitor, if that does not fix things, boot the Live CD, install gparted, then plug in the flash drive.
Open gparted and select the flash drive. It should show how much space is left in each partition.
You might need to shrink FAT32, /home or swap and then expand /.

---

