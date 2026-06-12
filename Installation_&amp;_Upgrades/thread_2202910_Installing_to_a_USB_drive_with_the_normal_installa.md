---
title: "Installing to a USB drive with the normal installation method rather than with Univer"
date: 2014-01-31
forum: Installation &amp; Upgrades
---

### Post by mongoose00318 on 2014-01-31
Hello,

I have tried installing Ubuntu (as well as other distros) to a USB drive with persistence, using both Universal USB Installer and Unetbootin. Both worked alright but with issues. The Universal USB Installer worked the best. But, even then I still had issues. I had issues installing software on it...some would work, some would work partially, and some just flat out didn't work well at all. One example of an application(s) that I tried to install that didn't work well was when I was trying to install LAMP. 

I followed the instructions on this article - [http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/)

When I got to this point,
 
Now check if[FONT=arial] php is working :
[/FONT]
 **[FONT=arial]$sudo vi /var/www/info.php[/FONT]** [FONT=arial]and add[/FONT]
 **<?php**
**phpinfo();**
**?>**

I couldn't add the code to the file or whatever the article is saying you need to do..granted that article isn't the most specific or the best article out there. I've since found several that are much better. But, again, this isn't the only piece of software I tried to install to the USB drive that I had issues with. 

I had issues trying to setup a user account. What I mean is, I setup a user account with a password and administrative privileges and anytime I booted up the drive it would never ask for the password. It would just go right into the OS without any kind of prompt or password protection at all. I had troubles getting "Everpad" to work correctly. I had issues emptying the trash when I would delete files which caused the drive to end up filling up rather quickly.

My conclusion was that 1) little issues here and there were probably to be expected since it was a USB install and 2) some of these issues might have been happening because from what I understand, it's running the OS as a live CD (but with persistence via Casper), so some of the issues I may have been having could have been related to that (ie. the user account/password issue I was having).

My question to you is, is there a way to either solve these issues (I know I may need to be more specific on the details issue by issue) or instead just install Ubuntu the normal way as if the USB drive was the hard drive I was going to install the OS to?

Any help, comment, or experience you can contribute to this thread is much appreciated! TIA!

P.S. I just joined this forum and it's long overdue so, hello everyone! I look forward to joining the community!

Thanks!

mongoose

---

### Post by monkeybrain20122 on 2014-01-31
> **mongoose00318 said:**
> Hello,

I have tried installing Ubuntu (as well as other distros) to a USB drive with persistence, using both Universal USB Installer and Unetbootin. Both worked alright but with issues. The Universal USB Installer worked the best. But, even then I still had issues. I had issues installing software on it...some would work, some would work partially, and some just flat out didn't work well at all. One example of an application(s) that I tried to install that didn't work well was when I was trying to install LAMP. 

I followed the instructions on this article - [http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/)

When I got to this point,
 ...

If you install into a usb drive it would work. But you do not, you are running a live session which is not a real install, something may not work..  A live usb is for installing and for testing, it is not meant to be a replacement of a real installation.

---

### Post by mongoose00318 on 2014-01-31
Is there anything specific I would need to do during the installation process to be sure that it would work from one computer to another?

I basically want it as a mobile development OS that I can have with me on the go. It would have the tools that I use for development on it with maybe a couple of other tools but I wouldn't use it for a lot of storage. I would store files on an ext. HD or something like that.

---

### Post by C.S.Cameron on 2014-01-31
You can use the following as a checklist for installing 12.04 to USB.
12.10, 13.04 & 13.10 are similar.

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language.
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
Select "Primary", "New partition size ..." = 4500 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.

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
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You may do an update-grub later.

---

### Post by Bucky Ball on 2014-01-31
[QUOTE=C.S.Cameron]Select Download updates while installing and Select Install this third-party software.[/QUOTE]

Third party software may not be required for the purpose this is going to be put and may be a waste of space on a dongle. ;)

I would personally leave these unticked (can sometimes cause issues, anyway) and update when installed. Add third-party software as/if required later.

---

