---
title: "How to create a persistent Ubuntu USB accessible from windows?"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by madsc89 on 2011-03-24
I want to create a combined portable Ubuntu / USB stick.

For this I intend to install Ubuntu to my 16 GB USB Drive. I am going to install some rather big programs (Matlab, Maple...) and therefor, I think the 4 GB persistent space in different startup-USB creators are to small.
Because of this, I want to install Ubuntu to the USB drive, to get full functionallity. Also because of the small USB Drive size, I dont want to create two different partitions. For USB Drive use, I want to be able to save files larger then 4 GB (ie. not FAT32).

The question: How can I create a fully functional Ubuntu USB, that can also be accessed from Windows?

I understand that NTFS and Ubuntu is a bad mix, FAT32 have file size restrictions, and Windows cant accesss ext3/4.

I saw someone talk about installing Ubuntu using the 'install in windows' to bypass Ubuntu-NTFS problems, but the link was broken, and I could not see how it was done. Also this ( [http://ubuntuforums.org/showthread.php?t=925288](http://ubuntuforums.org/showthread.php?t=925288) ) talked about making the home folder accessible, but the linked site is now down.


Any ideas?

Thank you.

---

### Post by oldfred on 2011-03-24
I have a full install of Natty in my 16GB flash and a 7.9GB data partition. Mine is set as ext4, but I do not see why it could not be NTFS and the NTFS as the first partition. Then windows should see it.

```
/dev/sdd3             7.9G   19M  7.4G   1% /media/KingstonData
/dev/sdd2             7.0G  3.7G  3.0G  56% /media/natty

```

---

### Post by C.S.Cameron on 2011-03-24
You can make a persistent casper-rw partition of any size, see part 1:
I also have a 4GB flash drive with Full install and FAT32 first partition for Windows access, see part 2:

**Part 1**
Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and add "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

**Part 2**
Check MD5SUM of the Ubuntu iso file.
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
(Optional partition for use on Windows machine)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 400MB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 2.77GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 600MB, Beginning, Ext2, and Mount point = "/home" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by madsc89 on 2011-03-25
Thank you both for the reply. I realize that I may have to settle with two partitions, however, I am not giving up just yet.
I really want to avoid splitting it into different partitions, as that would significantly cap either the ability to install programs or use it as portable storage on windows machines. I want the drive's free space to be available to both uses.

Is it possible to accomplish this?


I saw someone talk about useing the install inside of windows function, and then manually edit the mbr to make it bootable. However, I lack the technical know how to work out the details. Any suggestions?

Thank you.

---

### Post by beew on 2011-03-25
I want to mention two things.

1)While full installation on USB is do-able, it tends to be quite slow especially for updates and install. If you want performance you should install on an external hard drive.

2) I don't know about Matlab and Maple but I have tried to install Mathematica on an external drive and use it as a portable but it didn't work. Mathematica would only run when I booted into the same machine that created the installation. If I booted from another machine Mathematica would demand a different license. I think it may be the same way with Maple and Matlab.


> I saw someone talk about useing the install inside of windows function,  and then manually edit the mbr to make it bootable. However, I lack the  technical know how to work out the details. Any suggestions?
That would be WUBI, but why would you want to do that?  That is not a real Linux installation, basically just a demo installed in Windows.

I have a multiboot external hard drive (2 Ubuntus, Fedora and another Linux) For Ubuntu10.10 basically 2 ext4 partitions, one as / the other as /home (15 G and 40G respectively) I use it as a portable on many different machines and there is no performance lag.

I can acess Windows from it  but I don't want Windows to be able to access it so I have no NTFS partition (so I can store Windows files in there, just have to fetch them from Ubuntu instead of putting them there from Windows)

---

### Post by madsc89 on 2011-03-25
1: The main aspect is portability. I have a USB stick, which I would also like to have ubuntu on.

2: With Matlab, I am just going to have to see what happens.. Maybe it works, maybe it doesnt. 

I really dont want to be bothered by set pertition size limits. If I were to simply create one Ubuntu partition and one portable memory partition, it would be simple.
However, I want to be able to use all of the unused space to either Ubuntu programs (or files, settings etc.) or for storage accessible from windows. And this should be flexible, so that the USB stick's total unused space is there when I need it. 

Is there perhaps a way to not limit partition sizes, so that I could make my /home NTFS, and both / and /home can access all unused space?

If not, I am stuck with making the entire Ubuntu partition readable from windows?

This is on a USB stick with 12/30 MB/s write/read, and pretty poor random write/read. Perhaps the drawbacks of using bad file systems is not noticable, as the USB stick is already the bottleneck?


Some more or less random thoughts.. It would be really nice if its doable.

---

