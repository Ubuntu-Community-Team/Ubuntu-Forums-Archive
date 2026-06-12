---
title: "Problem installing ubuntu along side windows 10"
date: 2016-09-18
forum: Installation &amp; Upgrades
---

### Post by samsha33 on 2016-09-18
I have upgraded to windows 10 from windows 7. Now I'm trying to install Ubuntu 16.04 alongside windows 10, but on the installation screen ubuntu says "This computer has multiple OS on it" but I have windows 10 only . :(
To proceed i only have two option 1> Erase 2> something else.....i dont get the option of "Install alongside windows 10"
When i proceed with something else it shows me this screen
[ATTACH=CONFIG]271248[/ATTACH].
I only have two drives C and E ...sda2 and sda4 respectively.Windows 10 is installed on Sda2 but window 7 loader is detected there.
Please healp me out...:(:(:(:(

---

### Post by ajgreeny on 2016-09-18
Hi samsha33 and welcome to the forum.

I recommend that you boot to Windows first and use its own disk management utility to shrink your Win 10 partition and make room for Ubuntu. Do not create a new partition in Windows but simply leave the empty space. Now run chkdisk (or whatever it's called) from Windows a couple of times to make sure that is still running as it should.

I suspect the apparent two versions of Windows you see are simply a result of the upgrade adding a new bootloader system for Win 10 in the first small partition, sda1, but not renaming the Windows 7 partition, sda2. I note you have a very large fat32 partition sda4, which I assume is a data partition, not an OS itself; why fat32 which is an old and rather outdated filesystem nowadays?

That will leave you with unallocated space which you will see when you are installing Ubuntu, and I suggest you use the "Something Else" option when you get to that point which will give you full control of everything going on.

Have a good read of the page at [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html) and from about half way down this you will see various examples of installing 14.04 using "Something Else" to install 14.04 both singly and in dual boot; 16.04 may look a little different but is basically the same procedure.

Good luck and come back if you need more help.

---

### Post by Impavidus on 2016-09-18
Excellent advice above from ajgreeny.

Also note you've hit the 4 primary partition limit. I see no EFI partition, you must be using MBR partitioning, as is usual with Win7. This means you can have at most 4 primary partitions. You already have those: a small NTFS partition that is needed by Win10, the main Windows partition, a small NTFS partition (recovery maybe?) and a huge fat32 partition. That last one is a bit strange, as fat32 isn't really fit for those large partitions (still serves a good role on small usb drives, but for internal hard drives fat32 is outdated). You have to remove one of those partitions or convert it somehow to a logical partition, or you'll be unable to add a partition for Ubuntu. Be careful not to let Windows change to dynamic partitions.

---

### Post by samsha33 on 2016-09-18
About the Fat partition,that drive was not created by me I just extended the drive. Hp provided the drive with Quick web installed on it... Now i changed it to NTFS.....Thanks for mentioning.
Now about my problem , is there any way to remove that win 7 loader?
I tried severall methods but I only can see windows 10 bootloader.NO traces of win 7 to delete or modify

---

### Post by ajgreeny on 2016-09-18
> **samsha33 said:**
> About the Fat partition,that drive was not created by me I just extended the drive. Hp provided the drive with Quick web installed on it... Now i changed it to NTFS.....Thanks for mentioning.
Now about my problem , is there any way to remove that win 7 loader?
I tried severall methods but I only can see windows 10 bootloader.NO traces of win 7 to delete or modify
No idea about that I'm afraid, as I don't use Windows any more.

If that old fat32 (now ntfs) partition is just data and not OS you could back up all the data on it and use that space as a new extended partition in which you can create a new logical partitions, a ~20GB ext4 partition for your Ubuntu root and a 2GB swap.  Your home can then stay in root and you can use the ntfs partition to restore your backe4d up old data folders and files, and you could also could create symbolic links from those data folders to files in your Ubuntu home folder.

Come back and ask again if you need to regarding the symbolic link possibility.

---

