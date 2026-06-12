---
title: "How to Dual boot Ubuntu + WinXp using a second Hard-drive"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by linuxmaveric on 2007-01-26
I am a new convert to Linux and Im using Ubuntu 6.10.  I will be installing a second hard-drive for Ubuntu (100gb ATA Seagate).  Im making Ubuntu my slave drive.  I'll be using grub for booting. Or should I use WinXP boot menu?  Can anyone help me with a step by step explanation of how to get this accomplished with the least interference with my XP.  Or direct me to a website that covers this process.  My wife will continue with the XP and Im Linux all the way.  She will kill me if our XP corrupts due to the dual boot process :)  I have already backed up my XP files, and Im ready to install my new hard-drive, and hopefully have Ubuntu ready to go in the coming weeks.  This is a great forum and awesome community.  I hope to convert my wife to Linux soon.

Wish me luck.

Raul, Jr.

---

### Post by Jimmey on 2007-01-26
It depends upon what's going on already :-)

If it's your intention to have Ubuntu on the second 100GB hard drive that you mentioned, then after its installation, you can just install Ubuntu right onto it. Ubuntu's installation process will pick up on the fact that Windows XP is already there, and will make sure that it's selectable as a boot option from the GRUB menu.

---

### Post by confused57 on 2007-01-26
> **linuxmaveric said:**
> I am a new convert to Linux and Im using Ubuntu 6.10.  I will be installing a second hard-drive for Ubuntu (100gb ATA Seagate).  Im making Ubuntu my slave drive.  I'll be using grub for booting. Or should I use WinXP boot menu?  Can anyone help me with a step by step explanation of how to get this accomplished with the least interference with my XP.  Or direct me to a website that covers this process.  My wife will continue with the XP and Im Linux all the way.  She will kill me if our XP corrupts due to the dual boot process :)  I have already backed up my XP files, and Im ready to install my new hard-drive, and hopefully have Ubuntu ready to go in the coming weeks.  This is a great forum and awesome community.  I hope to convert my wife to Linux soon.

Wish me luck.

Raul, Jr.

You might want to consider setting your system up this way:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by linuxmaveric on 2007-01-27
Thanks for the tip. Im going to install ubuntu 6.10 in the next hour.  Wish me luck!

Thanks :)

---

### Post by linuxmaveric on 2007-01-27
I found this link on the web and it was very helpful explaining dual boot configuration. Hope this helps out anyone looking to install ubuntu & windows.

:)

Illustrated Dual Boot Site
Home Page


Edited 16th December 2006


This website is for people who have another operating system in their computer already and want to add a Ubuntu Linux operating system. 

This website is about how to use the Ubuntu 'Dapper Drake' and 'Edgy Eft' Alternate' Install CDs. 
The 'Alternate' Install CD features the more traditional text based partitioner.  
The main advantage of using the 'Alternate' install CD is that more choices are available for people who want to control the installation more precisely to  customize their install.
For example, you can choose between GRUB and LILO bootloaders and also specify exactly where you want the the bootloader installed. You can install the IPL for the bootloader to MBR on your first hard disk or any other hard disk you specify, or to the bootsector of the partition, or to a floppy disk or anywhere. You can even choose to continue the installation with no bootloader at all if that's what you want.
The 'Alternate' CD's installer does not require a huge amount of installed RAM in a machine either. I have used it plenty of times to install in a computer with 128 mb of memory.

Disadvantages of the 'Alternate' CD as opposed to the 'Desktop' graphical installer are that you can't 'see' what you are doing. There isn't a bar graph you can look at representing your hard disk. There are also a few extra choices and decisions to make. This confuses some people. I made this website to help show people the ways to navigate through the installation process, so anyone can do it.

This website shows an illustrated example of the Ubuntu Linux 'Edgy Eft' edition operating system being installed 'dual boot' with another operating system having a FAT32 filesystem. This would apply to Windows XP or earlier Windows editions. 

There are two examples of Ubuntu 'Dapper Drake' being installed with Windows XP having the NTFS filesystem. 

The install CD used for the 'Edgy Eft 6.10' install is ubuntu-6.10-alternate-i386.iso,md5sum 549ef19097b10ac9237c08f6dc6084c6

The install CD used for the 'Dapper Drake 6.06' installs is  ubuntu-6.06-alternate-i386.iso,md5sum b2e9120f06d70cc076c1852c6c04654e

This website is not about the 'Desktop' Live/Install CD's installer.
The Ubuntu 'Edgy Eft' 'Desktop' Live/Install CD features the Gparted graphical partitioner. That one is recommended for most people, it is lot simpler to use. 
The install CD used for that type of install would be the same as  'Ubuntu-6.06-desktop-i386.iso'. For help with Dapper Drake 6.06 install from the new Dapper Live/Install CD, (ubuntu-6.06-desktop-i386.iso), I recommend Aysiu's webpage, [http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)
There is also a wealth of other information at aysiu's site for after the install is finished, especially for helping new Linux users who have just joined us. Even more experienced users are likely to learn something, visit  [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) 

          
This website contains examples of what the I (the author) have tried and tested and found to work on my own machines. Since every computer in the world is different, it is obvious that many aspects of an operating system installation will vary quite a lot between one machine and another. The information on this site is not to be taken as instructions. You may find it handy though, to see how I do things so you can decide how you can do something similar. Just be aware that you will need to use your own common sense and good judgment at all times and make sure whatever you do is appropriate for your machine. 
Neither the author of this website nor the producers of any of the softwares being described on this website can be held responsible for any data loss or damage to any machine, whether electronic or otherwise, that may be caused by following any of these examples. Use this information at your own risk.

But having said that, malware and virus writers are not very responsible either, so make up your own mind which you'd rather have, Linux is practically immune from most of those threats. If you use Linux for all your web browsing and receiving e-mail, you can protect your Windows system from harmful exposure to the internet. At the same time you can learn how to do lots of new tricks that only Linux operating systems can do. You can avail yourself of hundreds of free software programs and applications too, that would be worth thousands of dollars if you had to pay for them.
Eventually most people end up migrating to Ubuntu Linux as they learn how to use it and realize how many more functions they can have at their disposal and how secure it is.

This is not an official Ubuntu Website, I just present this web-site for a hobby. Ubuntu does happen to be my favorite Linux distribution and I want to help other people install it too.

If you want to see the Official Ubuntu HomePage, use this link:  Official Ubuntu HomePage

If you would like to visit Ubuntu Web Forums, here's the link: Ubuntu Web Forums

For the Official Ubuntu Wiki for the genuine instructions: Official Ubuntu Wiki Front Page
Click on 'User Documentation', then 'Installation', and choose an appropriate link from there.

This website's install pages should come very close to illustrating the installation instructions to be found in the official Ubuntu Wiki. If you find something different, then please use your own judgment, and follow the instructions in the Official Ubuntu Wiki if still in doubt.
Some of my other pages do differ somewhat from the Official Ubuntu Wiki, or cover topics not mentioned in the Wiki.
This site is for Linux beginners and experienced users as well, so there are some things here to help people who are just getting started. 


INDEX

Illustrated Dual Boot HomePage....................................................................(you are here already)


Getting prepared:

How to Uninstall Ubuntu................(start here)........................................................Un-install Page

BIOS page (boot sequence)...............................................................................................BIOS Page

Pre-install Page..............................(read this before beginning any install).........Pre-install Page


The three illustrated example installs:

Windows with FAT32 file system and Ubuntu (Edgy Eft).........................................Ubuntu+FAT32

Windows with NTFS file system and Ubuntu (Dapper Drake)...................................Ubuntu+NTFS

Windows w NTFS and Ubuntu with Seperate Home (Dapper Drake)......................Seperate /home


Some things you might want more information about:

sudo dpkg-reconfigure xserver-xorg...........................................................................Xserver Page

MBR Page............................................................................................................................MBR Page

GRUB Bootloader Page....................................................................................................GRUB Page

GAG Boot Manager Page..................................................................................................GAG Page

Super Grub Disk Page....................................................................................Super Grub Disk Page


Things you can do after your install:

Post-install Page...................................................................................................Post-install Page

Mount Other Filesystems..................(under construction).....................................Mounting Page

SSH Network................................................................................................................SSH Network

Back Up and Restore.....................................................................................Back Up and Restore

 
If you have more than one computer, it is easy to refer to pages of this site in one computer for help while performing operations in another computer nearby.

If you have only one computer, it might be handy to print out one of these web pages so you can refer to it while you are installing. Just click 'File'-> 'Page Setup', and then , 'File'-> Print Preview'. If you are happy with it, click 'Print'. That should work for most browsers.
If these pages come out in color, they might use too much ink. You might be able to 'Select all' and copy and paste the text and illustrations only to a Word document, or right click on a page and 'Save Page As' if you need to and remove the background color somehow first before printing anything out.
Here's the link to this site:  [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by une on 2007-01-27
I have had a dual OS/dual HD setup with Mandrake 10 Linux and Win XP for a few years. Each OS has its own HD. I found that the more separation between the two OSs, the better. Therefore I change the boot order in BIOS depending on which OS I want to use. It is a tiny bit of work when starting up, but a very simple procedure that you only have to carry out if you want your session to be on a different OS to your last session. Despite what many have told me, I have found that without a deep understanding of boot loaders etc, Windows and Linux always have hassles with each other. 2 HD and 2 OS with BIOS being used to choose OS for the session is the ultimate in compartmentalization of the 2 OSs. It has worked for me.

---

### Post by linuxmaveric on 2007-02-04
I did it!! I finally got my Ubuntu installed.  Thanks for everyones help.  I just finished downloading the updates, and Im off to the internet via Linux Ubuntu.  Wow...the firefox browser is lighting fast.

RR :)

---

