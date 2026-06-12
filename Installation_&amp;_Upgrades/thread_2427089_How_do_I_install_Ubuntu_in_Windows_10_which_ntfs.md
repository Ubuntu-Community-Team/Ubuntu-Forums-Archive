---
title: "How do I install Ubuntu in Windows 10 which ntfs ?"
date: 2019-09-17
forum: Installation &amp; Upgrades
---

### Post by tangara on 2019-09-17
I managed to 'burnt' the image onto a USB stick this time round.

And able to reboot using USB stick.

My next step is to install Ubuntu to a partitioned disk in Windows 10 system.

However, I am not sure which sda and the dropdown menu - device for boot loader (can I skip this part - as I am ok to start Windows normally) to select.  Please see attached picture.

As a precaution, I need to be sure cos I don't want to lose all the data in my C:\

Can someone advise me how to know which one to select ?

---

### Post by oldfred on 2019-09-17
You are making major changes to system. You must have good backups.
       Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
More backup info from 1clue
[https://ubuntuforums.org/showthread.php?t=2377810](https://ubuntuforums.org/showthread.php?t=2377810)
[https://askubuntu.com/questions/569679/whats-a-good-back-up-strategy-for-1-desktop-pc](https://askubuntu.com/questions/569679/whats-a-good-back-up-strategy-for-1-desktop-pc) 
    
Please post terminal output, rather than screen shots if possible. And if longer use Code tags which are easy to add with Forum's advanced editor and # icon.
sudo parted -l

It looks like an UEFI install. If drive is gpt, then Windows has to be in UEFI boot mode.
See link below in my signature for lots more info on UEFI install.

If UEFI, Ubuntu's Ubiquity installer only install's grub2 boot loader to ESP on first drive it sees. With Windows it then normally shares the same ESP - efi system partition as Windows.
But you normally select a drive like sda or nvme0n1, not a partition like sda2.

---

### Post by mastablasta on 2019-09-18
i would recommend first trying it in virtualbox. for example here is one such guide: [https://www.psychocats.net/ubuntu/virtualbox](https://www.psychocats.net/ubuntu/virtualbox)

Ubuntu is an os and is not really installed inside windows but next to it.
this (the WSL) is likely something else than what you want as it is just a terminal: [https://tutorials.ubuntu.com/tutorial/tutorial-ubuntu-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-ubuntu-on-windows#0) 
Windows Subsystem for Linux Installation Guide for Windows 10: [https://docs.microsoft.com/en-us/windows/wsl/install-win10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

As an OS it uses it's own file system (there are a few to choose from Ext4, BTRFS, ZFS...) and for that it needs a separate disk partition and space.

---

### Post by tangara on 2019-09-18
Hi,

What do you mean by UEFI install ?

Basically, I am following this tutorial :

[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0)

and 

[https://www.tecmint.com/install-ubuntu-alongside-with-windows/](https://www.tecmint.com/install-ubuntu-alongside-with-windows/)

But, I am actually stuck cos I am not sure if I should use /root or should I use /

and also what is the device for boot loader installation I should go for ?

Can someone advise me ?






Thanks.

---

### Post by (kyT%0) on 2019-09-18
> **tangara said:**
> what is the device for boot loader installation I should go for ?

ideally it should be your primary hard disk / sda.

---

### Post by yancek on 2019-09-18
The image in your initial post shows a fat32 partition which would indicate an EFI install as suggested above.  That image also does not show any free space on which to install Ubuntu which would indicate that you skipped the first step in the tutorial from the link you posted, namely to shrink the largest windows partition with Disk Management.   Installing any Linux OS on an ntfs formatted partition won't work.  After doing that, you should reboot windows to verify that it still boots before trying to install another OS.

I would suggest you read the Ubuntu documentation at the link below on dual booting with windows 10 prior to trying to install.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Selecting to install the Grub bootloader to /dev/sda in your case should create an Ubuntu directory in the EFI partition which will contain the necessary boot files.

Any time you are installing another OS or changing partitions, you need to have complete backups of any data important to you.

---

### Post by TheFu on 2019-09-18
Dual booting is dangerous to every OS on the system.  Before doing this, please have excellent backups.  There's a 50/50 chance you'll need them. As you learn more and gain more practice+understanding, that risk is reduced, but it will never become 0.  Experts with dual booting have issues booting one of the OSes about once a year, usually thanks to MSFT breaking it.

Using a virtual machine is much safer, since it uses a virtual HDD that is really just a large file on the main OS on the system.  For safety reasons, assuming  the  computer isn't 10+ yrs old and has normal RAM + CPU performance, using virtualbox is probably the best way to introduce yourself to Linux.

---

### Post by tangara on 2019-09-22
> **TheFu said:**
> Dual booting is dangerous to every OS on the system.  Before doing this, please have excellent backups.  There's a 50/50 chance you'll need them. As you learn more and gain more practice+understanding, that risk is reduced, but it will never become 0.  Experts with dual booting have issues booting one of the OSes about once a year, usually thanks to MSFT breaking it.

Using a virtual machine is much safer, since it uses a virtual HDD that is really just a large file on the main OS on the system.  For safety reasons, assuming  the  computer isn't 10+ yrs old and has normal RAM + CPU performance, using virtualbox is probably the best way to introduce yourself to Linux.

If I do not have go for dual booting, what is the alternative ?

What if I buy a SSD and use that for Linux operation only?  Will that be feasible when most of my stuff are in Windows 10 ?

---

### Post by tangara on 2019-09-22
Hi,

I actually have ample space - Please find attached - the SD4 is the one which I have allocated 40000MB

In this case, what would be the device for boot loader installation ?

Also, I saw an error but I am not sure what it means.  Could you/anyone advise me on that ?

And I have problem in backing up my files cos it's been 10 years and no matter what I delete, my external hard disk doesn't have the space.

Would you advise me to use SSD for running my linux instead?  However, I am not sure if my IDE, database etc are all in Windows 10, will it be able to operate - for eg. I want to use Linux command to install a new software and it is to be used with my database - PostgreSQL but this database is installed in Windows 10.

---

### Post by yancek on 2019-09-22
> the SD4 is the one which I have allocated 40000MB

As pointed out above (post 6), you CANNOT install Ubuntu (or any Linux) on a proprietary windows filesystem and the partition sda4 is clearly the largest partition and shows an ntfs filesystem.  You have not used Disk Management in windows to shrink that partition and leave unallocated space for Ubuntu.  That is necessary.  Reboot to windows to verify this worked and the OS still boots before trying to install Ubuntu.  I would again suggest you read the official Ubuntu documentation on dual booting UEFI with windows, link in post 6.  

> PostgreSQL but this database is installed in Windows 10. 		

 I don't use that software but I doubt it would work with the database on windows and you would need to install it on Ubuntu along with the database.  Might wait for someone more familiar with  PostgreSQL to confirm this.

---

### Post by tea for one on 2019-09-22
> **tangara said:**
> And I have problem in backing up my files cos it's been 10 years and no matter what I delete, my external hard disk doesn't have the space.

Please do not install a new OS until you have adequate backups. 

There are multiple threads on these forums where backups are missing and users spend hours/days with various data recovery tools.

---

### Post by TheFu on 2019-09-22
Backups are not optional.  If you don't have backups, fix that first.  All the posts about data recovery here usually end in tears.
Instead of dual booting,  ... 
> Using a virtual machine is much safer
which is what I suggested above. If you use virtual machines, then you can keep NTFS for the file system where the VMs virtual hard disks sit.  There are 10,000+ youtube videos about running and using virtual machines.  Google *virtualization* for more information.  Every place I've worked since the late 1990s has used virtualization.  Around 2006, they all started making VMs the default way to deploy servers and deploying directly onto hardware required CxO signatures.  The entire world has been running on virtual machines about 15 yrs.  Ever heard of "the cloud?"  Those are all either virtual machines or Linux Containers.  ALL OF THEM.

I can't read images.  Text please. No images.  If you are going to be using servers, then please learn the CLI commands to show relevant data.

---

### Post by Impavidus on 2019-09-23
The pictures are a bit hard to read (a photograph with large perspective distortion and aliasing of a broken screen, displaying not the most helpful GUI...), but I do see that you have 231GB unallocated space at the end of the hard drive. Scroll down in the list, select the free space, create a partition for Ubuntu. You cannot install Ubuntu on an ntfs partition, so the 40GB free space on sda4 is irrelevant. All of sda4 is allocated to Windows, so as far as Ubuntu is concerned, it's not free. That is, if you want to dual boot. Dual booting used to be easy and reliable, but it has become more fragile. If you boot the live system in UEFI mode, it should install the boot loader automatically to the EFI partition on the first hard drive.

And of course, everybody who has said that you have to make backups is right.

---

