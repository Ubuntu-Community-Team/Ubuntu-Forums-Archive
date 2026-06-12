---
title: "How does one install 10.10 to USB from Live CD?"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by at0msk on 2010-11-14
^
I have a 32gb flash drive that I'd like to install Ubuntu 10.10 too. As if it were just a normal installation. Boot loader and all just on the stick...

To note: I would be attempting this from a Windows system. I do have a burned copy of the Ubuntu 10.10 live CD.

---

### Post by Hegh on 2010-11-14
The USB Startup Disk creator should be able to do that for you. Just choose the CD image (if you have a physical CD then you will likely need to either rip an image using K3b or similar, or download one from the web site).

Make sure to allocate space on the USB drive for storage; the control for this should be near the bottom of the USB Startup Disk creator program window.

The USB Startup Disk creator program should be found under the System menu.

---

### Post by at0msk on 2010-11-14
> **Hegh said:**
> The USB Startup Disk creator should be able to do that for you. Just choose the CD image (if you have a physical CD then you will likely need to either rip an image using K3b or similar, or download one from the web site).

Make sure to allocate space on the USB drive for storage; the control for this should be near the bottom of the USB Startup Disk creator program window.

The USB Startup Disk creator program should be found under the System menu.


...Do you speak of the USB Startup Disk creator linked from the Ubuntu site? I'm not going for a live cd on usb but an actual install...

---

### Post by lmarmisa on 2010-11-14
[Flash memories]("http://en.wikipedia.org/wiki/Flash_memory") have some limitations related to block erasure or a finite number of program-erase cycles.

Due to these limitations, it is not recommended to install standard versions of Ubuntu in such devices.

So I recommend to use the USB startup disk creator option.

---

### Post by at0msk on 2010-11-14
> **lmarmisa said:**
> [Flash memories]("http://en.wikipedia.org/wiki/Flash_memory") have some limitations related to block erasure or a finite number of program-erase cycles.

Due to these limitations, it is not recommended to install standard versions of Ubuntu in such devices.

So I recommend to use the USB startup disk creator option.

>.>

---

### Post by oldfred on 2010-11-14
You can do a full install. You should do it more like a SSD where certain extra settings are required. But otherwise it is just like any install to a second drive. As with any install to a second drive be sure to install grub2 to the MBR of the flash drive, grub likes to install to sda or your internal. It is best to partition in advance and use manual install.

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
See post #19 C.S.Cameron ( But I do not unplug hard drive, just use advanced button to install to USB) 
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

---

### Post by lmarmisa on 2010-11-14
> **at0msk said:**
> >.>

Sorry, what does it mean?.

[http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)

---

### Post by at0msk on 2010-11-14
> **oldfred said:**
> You can do a full install. You should do it more like a SSD where certain extra settings are required. But otherwise it is just like any install to a second drive. As with any install to a second drive be sure to install grub2 to the MBR of the flash drive, grub likes to install to sda or your internal. It is best to partition in advance and use manual install.

Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
See post #19 C.S.Cameron ( But I do not unplug hard drive, just use advanced button to install to USB) 
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

Thank you. I have been trying to do a normal install with ext4 but it won't let me partition the drive for swap...the new partition table button doesn't do anything. I know swaps are optional but they are nice to have...

Do you think I should just disconnect the internal hdd? Or go with no swap?

---

### Post by at0msk on 2010-11-14
> **lmarmisa said:**
> Sorry, what does it mean?.

[http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html](http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html)


>.> is internet for glare. As in: "I appreciate your response but it wasn't what I was looking for." Just because one should not do something does not mean one cannot. Plus, it's a flash drive. Really... I don't expect it to last for the next 60 years or anything. It is not like I will be using it as my main workstation for hours on end some odd number of days of the week.

---

### Post by at0msk on 2010-11-14
bump for great justice

---

### Post by at0msk on 2010-11-14
bump for great justice

---

### Post by oldfred on 2010-11-14
I do not understand why you cannot create swap. Are you trying to add more than 4 partitions without converting one to an extended partition?

C.S.Cameron and a few others will tell you to disconnect drive to prevent any errors. I always said just look for advanced button to make sure you install grub to the external drive/device. But with Maverick they have made the grub advance button a combo button that only appears on manual installs.So removing drive may be safer.
But it is not all that difficult to reinstall boot loaders, and for new users it can seem intimidating. You do need to have liveCDs or USB keys with repair capability for whatever systems you use.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Just because I wanted to learn about gpt partitions instead of the old MBR(msdos) scheme I used gpt. It worked but I do not know if it gives any advantages except on drives over 2TB. My flash is 16Gb.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

---

### Post by at0msk on 2010-11-14
> **oldfred said:**
> I do not understand why you cannot create swap. Are you trying to add more than 4 partitions without converting one to an extended partition?

C.S.Cameron and a few others will tell you to disconnect drive to prevent any errors. I always said just look for advanced button to make sure you install grub to the external drive/device. But with Maverick they have made the grub advance button a combo button that only appears on manual installs.So removing drive may be safer.
But it is not all that difficult to reinstall boot loaders, and for new users it can seem intimidating. You do need to have liveCDs or USB keys with repair capability for whatever systems you use.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Just because I wanted to learn about gpt partitions instead of the old MBR(msdos) scheme I used gpt. It worked but I do not know if it gives any advantages except on drives over 2TB. My flash is 16Gb.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

Well in the installer for the live 10.10 CD one does not get an advance button. ;(

The only thing one gets is to set up partitioning manually. So far it's just a straight 32gb USB stick with no partitions on it. I hit Change and set the boot loader and the root. After that if I hit "new partition table" nothing happens. It appears to be an issue with the 10.10 installer rather than user error. I'll see about gparted for setting up swap space.

---

### Post by C.S.Cameron on 2010-11-14
Step by step for 10.10:

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


Doing the math, your flash drive should last years running ubuntu off it 8 hours per day.

---

### Post by at0msk on 2010-11-15
> **C.S.Cameron said:**
> 
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


Well for whatever reason it's working now. Could you explain the above portion further? The stick I am using is 32GB and I want to make the most of it. I see we're creating about 4 partitions here is that right? I'd just like a basic install of Ubuntu on the stick with the install in it's own partition and the rest of the space to just be there for the junk i'll pile on to it... Again the goal is to take this with me and be able to boot into my own "pc" from anything that supports booting from USB devices (of course without destroying the host machines mbr).

Also, how are your "optionals" placed?

> **C.S.Cameron said:**
> 
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.


Do you mean these are optional?

> **C.S.Cameron said:**
> 
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)


Or do you mean these are optional?

---

### Post by at0msk on 2010-11-15
So I guess three partitions here.

1) Ubuntu (roughly 4-6GB?)
2) Files (~24GB)
3) Swap (~1GB)

How would that look in the installer?

What about this? Am I close? lol

/dev/sda1 | ext4 | /         | 6199
/dev/sda5 | swap|           | 1198
/dev/sda6 | ext4 | /home | 24924

---

### Post by C.S.Cameron on 2010-11-15
All the partitions are optional except the ext3 or 4 /.
The FAT32 partition is for copying or saving files from a Windows computer. This should be the first partition on a flash drive. On a USB HDD you might want to format it NTFS.
A separate /home is not necessary is but handy if you prefer fresh installs over upgrades. 
Swap is also not absolutely necessary on a portable drive. I think it is necessary if you want the drive to be able to hibernate.

---

### Post by at0msk on 2010-11-16
> **C.S.Cameron said:**
> All the partitions are optional except the ext3 or 4 /.
The FAT32 partition is for copying or saving files from a Windows computer. This should be the first partition on a flash drive. On a USB HDD you might want to format it NTFS.
A separate /home is not necessary is but handy if you prefer fresh installs over upgrades. 
Swap is also not absolutely necessary on a portable drive. I think it is necessary if you want the drive to be able to hibernate.

Ubuntu reads FAT32 correct? So I should probably take the remainder and format it to FAT32? I also set that to /home because I was told that if I didn't set a place for it to mount from it wouldn't be used. With Windows I prefer upgrades but have the OS on it's own partition for fresh installs where needed. I figured with Ubuntu given it's size and versatility I'll be more apt to fresh installs.

```

/dev/sda1 | fat32| /home | 24924
/dev/sda5 | swap|           | 1198
/dev/sda6 | ext4 | /         | 6199

```OR

```

/dev/sda1 | fat32| /home | 24924
/dev/sda5 | ext4 | /         | 6199
/dev/sda6 | swap|           | 1198

```

---

### Post by at0msk on 2010-11-16
great justice!


:popcorn:

---

### Post by oldfred on 2010-11-16
NTFS & FAT do not support Linux file permissions and ownership. You cannot use windows file systems for linux file systems.

Linux will read and write the NTFS or FAT systems without any issue.

So /home has to be a linux file system not FAT32.

---

### Post by at0msk on 2010-11-16
> **oldfred said:**
> NTFS & FAT do not support Linux file permissions and ownership. You cannot use windows file systems for linux file systems.

Linux will read and write the NTFS or FAT systems without any issue.

So /home has to be a linux file system not FAT32.

OK so how should the partitions look then? Say I plug in the flash drive after the fact and want to access the drives of a broken windows system and grab files? What then? That's what I'd like the remaining space for. Given that the 6GB OS and 1GB Swap partitions exist what is my next step with the remaining 24GB? We've addressed what Linux/Windows can and cannot do now let's set up the partitions.

Would either of these then be sufficient?

```

/dev/sda1 | ext4 | /home | 24924
/dev/sda5 | swap|           | 1198
/dev/sda6 | ext4 | /         | 6199

```OR

```

/dev/sda1 | ext4 | /home | 24924
/dev/sda5 | ext4 | /         | 6199
/dev/sda6 | swap|           | 1198

```

---

### Post by oldfred on 2010-11-16
Since it is a flash drive I do not think order is important. Only if you ever wanted to directly copy files from windows, would you need a FAT32 partition and then it would have to be first as windows only sees the first partition.

Go back to my earlier post linking to Herman's site on special settings that are recommended for flash drives.

---

### Post by at0msk on 2010-11-16
> **oldfred said:**
> Since it is a flash drive I do not think order is important. Only if you ever wanted to directly copy files from windows, would you need a FAT32 partition and then it would have to be first as windows only sees the first partition.

Go back to my earlier post linking to Herman's site on special settings that are recommended for flash drives.


OK I'll try this out then. I don't really see myself using it in a standard flash drive way where one would plug the stick into a Windows pc and start dropping files onto it. It'd be more of me booting into Ubuntu and pulling files from the Windows system.

---

### Post by C.S.Cameron on 2010-11-16
I think you have a good starting point, you can always adjust your partition sizes later with gparted.

I always find a small FAT32 partition as first partition useful though.
I try to avoid mucking around in other peoples Windows partitions while booting my Ubuntu flash drive whenever possible.

---

### Post by at0msk on 2010-11-17
> **C.S.Cameron said:**
> I think you have a good starting point, you can always adjust your partition sizes later with gparted.

I always find a small FAT32 partition as first partition useful though.
I try to avoid mucking around in other peoples Windows partitions while booting my Ubuntu flash drive whenever possible.


:D Well this all worked. I now have a bootable USBuntu stick. One question still remains. I believe /home is the Home folder in Ubuntu? Is that right? So if /home is its own partition things in the Home folder won't be lost if the OS partition is wiped right? 

I set up the 25GB partition as ext4 and told it to mount from /home. Is my logic correct?

---

### Post by oldfred on 2010-11-17
As with any reinstall, you would have to specify which partition is /home and then be careful to not format it. Normally you specify format as part of a reinstall for / and if any other separate system partition.

---

