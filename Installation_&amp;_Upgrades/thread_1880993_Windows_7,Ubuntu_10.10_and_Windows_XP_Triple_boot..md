---
title: "Windows 7,Ubuntu 10.10 and Windows XP Triple boot..."
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by TheDevilYouKnow on 2011-11-14
Hey Guys, I have a few questions about Triple booting.
 
I have three different physical hard disks in my system. Disk O is a 72 gig Raptor with Windows 7, Disk 1 has Ubuntu 10.10 on it, and Disk 2 Is my 1 TB data drive.
 
I have GRUB installed and the system is very stable and dual boots just fine off of Disk 1.
 
That being said I want to make a new partition on Disk 1 and install Windows XP on the same disk with Ubuntu 10.10...
 
Can I do this With Windows 7 on a separate drive ? Should I disconnect the Windows 7 drive physically and then try ? Can this even be done and If so where should I start?
 
 
Thanks Guys...

---

### Post by darkod on 2011-11-14
You can do it in number of ways, but the following is important: when installing more than one version of windows, it combines the boot files. So, by installing XP it will put the XP boot files on the win7 disk. If you remove this disk later, or format, XP can't boot.

Because of this it's better if you disconnect the win7 disk and install XP. It will put the boot files on the same disk in that case. Also make sure this disk is set up as the first option to boot from in bios because windows puts the files on that disk.

Then connect the win7 and do the ubuntu install. It should work fine.

Of course, you will first need to make room for XP on disk1 but you probably planned to do that.

---

### Post by TheDevilYouKnow on 2011-11-14
Thats pretty close to what I thought..

However Ubuntu is already installed on Disk 1. Should I wipe it out, then install XP ( after disconnecting Disk 0 ) and then install Ubuntu? 

Is there a way ti install XP with Ubuntu already installed on Disk 1? 

...And, should I update GRUB after the install of the new OS and again after I re-connect Disk 0? or Wait until everything is installed,re-connect all drives and then boot into Ubuntu and then update GRUB?

Thanks Again!

---

### Post by oldfred on 2011-11-14
XP should install to a primary partition formated to NTFS and with the boot flag set on that partition. Windows 7 has had some issues with gparted NTFS formated partitions, but XP has worked for most. Do you have a primary partition available (sda1 thru sda4)? Also if drive number changes the boot.ini may not be correct. It will be rdisk 0 and may not be when you plug the other drives back in. 
On a sudo update-grub, grub tries to do a mapdevice to correct windows drive numbering issues, but that may not always work.

To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

