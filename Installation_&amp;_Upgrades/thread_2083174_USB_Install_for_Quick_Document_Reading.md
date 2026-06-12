---
title: "USB Install for Quick Document Reading"
date: 2012-11-11
forum: Installation &amp; Upgrades
---

### Post by esnelling on 2012-11-11
Most grateful to the wonderful Linuxelite who has figured the solution to this challenge already.  I have spent the better part of a day researching, searching, trial-nd-error, and searching more but cannot get a solution to this problem:

What I need to do is use a laptop for quick document viewing of a USB directory that has data files synchronized on a weekly basis.  Laptop has a corporate Windows XP install and the normal boot time is 5-7 minutes which is unacceptable for what I need; unfortunately the hard drive is under SafeBoot so I think inaccessible from Linux.  So my solution is to boot the laptop into Linux using the same USB with the data files I need to read.  I do not need any advice on the data synch to USB :-)  Due to some restrictions the laptop must be completely OFF (Standby is unacceptable) from when I need to start accessing the files.  I would like to boot from the same USB as where I have the data files, but I have made perhaps 100 attempts to get the partitioning and bootloader working correctly - nothing but failure.  I should probably mention that I am operating under the assumption, from what I have read, that it is best to have my data files in one partition and the Linux install in the second partition.

Based on that this is what I think my requirements are:

[LIST=1]
[*]Load Linux from 16GB USB in under 60 seconds (Ubuntu is fine and what I am most familiar with)
[*]Install must be persistent with may 1GB or so for that
[*]Rest of space needs to be in the first partition of same USB so that it can be used normally on a Windows laptop
[/LIST]
After hours of searching, I am surprised that I cannot find a Linux Distro designed just for a quick boot into a document reader?  Maybe I missed it.  The laptop I am using is a Dell Latitude E6400 -- so I have consider Latitude ON (I think that's the name) but have deemed it unacceptable for what I need.

Thank in advance for any ideas.  If I am trying to do this the hard way, I am open to any solution you think might work better -- except an Ipad :-)

---

### Post by esnelling on 2012-11-18
No responses to date.  Perhaps I've posted in the wrong spot or am on the wrong track.  Could anyone please suggest a better OS solution for quick booting for the sole purpose of document reading on a laptop?  I thought Linux would be the ticket but maybe there is a better OS for this purpose.

Thank You.

---

### Post by C.S.Cameron on 2012-11-18
Following is step by step for installing 12.04 on a 8GB flash drive on an Intel machine. 12.08 is similar.
If all you need to do is read docs though, you might try Puppy.

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
Select "Primary", "New partition size ..." = 8000 to 12000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.
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

### Post by coldraven on 2012-11-18
I just tried this out...
Download Puppy Linux (precise puppy) from here
[http://puppylinux.org/main/Download%20Latest%20Release.htm](http://puppylinux.org/main/Download%20Latest%20Release.htm)

I used Unetbootin to create  a bootable 1GB SD card from the .iso file

Puppy took about 60 seconds on it's first boot, you have to configure a few choices. Language, Location etc

I copied the link for "default writer abiword" from /usr/local/bin to  ~/startup using drag and drop from two open file manager windows.

On shutdown Puppy asks where to save your choices, it found 850 MB free on the SD card so I selected that. 

The next reboot took about 50 seconds, it actually says on the screen that the next reboot will be faster. Abiword started automatically

The third reboot took about 40 seconds.

It's very very fast and has lots of useful applications, try it!
I might even use it as my main OS :)

---

### Post by esnelling on 2012-11-18
Thank you kind sirs; very much appreciate your time.  Pretty much gave up doing this on different partitions because Windows only recognizes the first partition and I can't figure how to get my Linux USB to boot from the second partition.  Using just a single partition, I almost have what I need but still struggling just a bit with the requirement to read/write documents on both a Windows and my Linux "reader" from the same USB.  Unfortunately, it seems some of my documents need "write" permission and I can't figure how to change this.

sudo chmod -R a+w mydocs_directory_on_usb

This command gives no errors but is unsuccessful in changing the permissions.  This is on the Ubuntu Live default mount location of /cdrom.  When I try to manually set a different mount folder, it just reverts back to cdrom.  I have probably just mangled some Linux terms here..sorry.

Thanks if anyone has any ideas or pointers for remedial training ;)

---

### Post by C.S.Cameron on 2012-11-18
Perhaps a Persistent install of Ubuntu or LUbuntu will suit you.
Everything is on one FAT32 partition.
You can read and write from Linux and Windows machines.
In order to access the files while booted from the device you need to go to filesystem/cdrom.
You can make a persistent install using UNetbootin or Startup Disk Creator, (from the Live CD).

My post above uses the first partition for Windows access and the second for running Ubuntu.
I looks complicated but is basically just the same as installing to internal drive.

---

### Post by esnelling on 2012-11-18
Thank you.  Yes a persistent install using Unetbootin is what I am using now.  Unfortunately I cannot seem to get the /cdrom permissions changed to write access.  Any ideas?  As mentioned above, I already tried chmod.

Oh thanks.  I will try the instructions in your first post.  If that will get the second partition to boot then that is exactly what I need; Thank You!

---

### Post by C.S.Cameron on 2012-11-18
Type Alt F2, Type 
```
gksu nautilus
```
you should now be able to write/read to /cdrom.

Edit:
Be careful while Root, a person can do lots of damage.

---

### Post by cwsnyder on 2012-11-18
Try C.S. Cameron's solution first.

Your problem is your mount point.  Mounting to /cdrom or /media/cdrom defaults to read-only.  Instead of mounting as a cdrom, you need to mount as a hard disk (/media/sdb1 or whatever you locate from the output of the terminal command of fdisk -l (lower case L)).

---

### Post by esnelling on 2012-11-19
THANKS EVERYONE.

Doing a full installation on the USB (per Cameron's instructions) was the ticket.  From previous experience I did not think the second partition would boot; but followed your instructions and voila; thanks.  My USB is a 32GB so need to rethink the partition sizes but other than that works just like I need.  Not sure why I struggled so long with the Live persistent method for so long.

Thanks again.

---

