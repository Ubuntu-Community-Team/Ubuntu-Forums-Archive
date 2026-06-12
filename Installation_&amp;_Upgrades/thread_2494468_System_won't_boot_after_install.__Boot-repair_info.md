---
title: "System won't boot after install.  Boot-repair info available."
date: 2024-01-17
forum: Installation &amp; Upgrades
---

### Post by oilhat on 2024-01-17
I have a dell inspiron 3252.  I removed the hard drive and replaced it with a different one.   
 
 
 I partitioned the drive with Kubuntu install usb stick.
 Then I installed windows 10.  Booted and worked normally.
 Then I installed Kubuntu 22.04.  I selected JFS file system during the install.
 Now it will not boot ununtu.  It goes to the grub command line and stops there.
Once I exit the grub command line, it boots to Windows.

 
 
 Bios settings were legacy option roms enabled during the install.  Boot was set to UEFI.  I have since disabled legacy option roms, but it didn’t change anything.  
 
 
  I booted from the kubuntu install usb stick and ran boot repair info.  Here is the pastebin.  [https://paste.ubuntu.com/p/NxbQYzvtCc/](https://paste.ubuntu.com/p/NxbQYzvtCc/)  What do I do next?

---

### Post by oldfred on 2024-01-17
Do not know jfs.

Grub does have a jfs.mod file. 
I would think installer should add a grub line like insmod jfs to your grub.cfg. 
Not sure if that has to be in the 3 line grub.cfg in ESP or in grub.cfg in your install. Or somehow incorporated otherwise.
[https://www.linux.org/threads/understanding-the-various-grub-modules.11142/](https://www.linux.org/threads/understanding-the-various-grub-modules.11142/)

---

### Post by oilhat on 2024-01-18
So perhaps I made a mistake selecting the file system during the manual  partitioning during the kubuntu install.  I almost forgot about JFS.   The files systems options are JFS, XFS, btrfs, and some others.  Rather  that try to insmod JFS and modify grub.cfg, or whatever, I reinstalled  kubuntu selecting XFS this time.  After the install, it boots.  Once the  install was completed and Kubuntu was running, I opened kde partition  manager and it shows xfs as the filesystem.  

I installed to  another computer a few weeks ago, and the filesystem is ext4.  I don't  recall what I selected during the install process, but it would have  been either JFS or XFS.  Are XFS and ext4 different names for the same  thing?  Is XFS the correct selection for basic kubuntu installation?  

Another  question about the manual partitioning step of the install.  There is a  selection for the location of the boot loader.  I selected /dev/sda and  it works.  But shouldn't the boot loader be on the efi partition which  is /dev/sda1?

---

### Post by oldfred on 2024-01-18
You always specify a drive for boot. With UEFI it automatically knows to use the ESP.
Ubuntu defaults to ESP on first drive.

Ubuntu default is ext4. Some other distributions use other file systems.

I do not have a more recent link, he typically does a review every year. But shows some of the differences between file systems.
Linux 4.16 File-System HDD & SSD Tests With EXT4/F2FS/Btrfs/XFS 2018
[https://www.phoronix.com/scan.php?page=article&item=linux-416-fs&num=1](https://www.phoronix.com/scan.php?page=article&item=linux-416-fs&num=1)
[https://ubuntuforums.org/showthread.php?t=2487352](https://ubuntuforums.org/showthread.php?t=2487352)

---

### Post by oilhat on 2024-01-18
Given that my other computer is using ext4 and ext4 is the default ubuntu filesystem, how do I perform the install so that the filesystem is ext4?  As I said earlier, ext4 is not an option in the manual partition step of the kubuntu installer.  The only selections are JFS, XFS, etc.  

Ext4 must be an option, since I got ext4 using the same kubuntu usb stick on my other computer.  I must have done something different last time.

---

### Post by ajgreeny on 2024-01-18
When you choose **Something Else** in the installation method and then highlight the partition in the installation window I think it defaults to "Do not use this partition" and you have to change that to "Use ext4 filesystem" or some similar wording (It's a while since I've done it and taken much notice as I do it so often and do not have to think about it any more; muscle memory!)

You must have missed that point in the install unless, of course, Kubuntu does things very differently from the other versions, but how you managed to get JFS I.m not sure; it's a filesystem I have never seen and  certainly never used for anything.

---

### Post by oilhat on 2024-01-18
Ajgreeny, you are right.  It defaults to do not use this partition.  Ext4 is an option, but I didn’t see it there because I didn’t scroll to the top of the list.  I guess I was in a hurry or something.  Meanwhile I have installed with JFS and XFS in an effort to get ext4.  I am installing for the third time now.  Hopefully I got right this time!

---

