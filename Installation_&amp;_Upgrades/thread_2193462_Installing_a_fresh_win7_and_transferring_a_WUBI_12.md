---
title: "Installing a fresh win7 and transferring a WUBI 12.04 installation to standard instal"
date: 2013-12-13
forum: Installation &amp; Upgrades
---

### Post by mmcl26554 on 2013-12-13
I am having an odd problem with win7 on my HP laptop. (the headphone jack will go dead and can only be restored by turning the computer OFF reboot doesn't work).   All attempts to fix this has failed including a new motherboard.  Now the only option is to reinstall win7 which also has WUBI 12.04.   I know and have studied how to transfer WUBI to a standard install and I believe I could do it to a  USB connected drive.   Should I install Win7 first or transfer Ubuntu first.   I have a backup of the original clean Win7 installation before I even booted the computer for the first time, so I am going to install that backup to the same USB connected drive.  After both win7 and Ubuntu are installed I will move the drive from a USB to an internal drive and finish installing all of my other win7 software and data that win easy transfer didn't.   So what suggestions do you people have for me?
Michael

---

### Post by Mark Phelps on 2013-12-13
I don't think you can install Win7 to an external drive.  That capability started with Win8 (Windows To Go) and only with the Enterprise editions.

---

### Post by mmcl26554 on 2013-12-13
The win 7 install I spoke of is not a traditional install but rather a copy of a backup of an virgin instal,l then move the Ubuntu WUBI install to that disk.   Then install the disk to the laptop and boot win7 to finish the startup and run windows easy transfer.    The main reason to do it this way is to facilitate the installation of Ubuntu from wubi to standard install.   I suppose I could do the wubi transfer to the bare disk and then transfer Ubuntu.   In any case my plan is to use Gparted to partition the drive for Ubuntu with a root and swap partitions and leave the unallocated space for windows.   I just need to know what is the best way to go for Ubuntu.   
Michael

---

### Post by oldfred on 2013-12-13
I am not well versed on details of wubi.
But I think you have to reinstall wubi and then copy your backup of root.disk back into the new install of wubi. A new install of Windows erases all traces of wubi since it is just a file inside the NTFS partition.

Much better to go to a partitioned install. Wubi is being discontinued as it does not work with gpt partitioned drives which all new UEFI systems have.
But with MBR partitioning you have to plan Windows for primary partitions and have one primary as the extended partition for the extra logical partitions you need for Linux.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

      
 HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

---

### Post by mmcl26554 on 2013-12-13
Oldfred,
The Original drive with wubi on it will remain in the computer until Ubuntu is transferred to the new drive which at the time will be a usb drive, then I will copy the new virgin win7 to the unallocated space on the new drive.   After that I'll install it in the laptop and finish the win7 setup.   The only problem I see is when I do the transfer of Ubuntu from a wubi to standard the drive names will be sdb1&2.  What happens when I move the drive to inside the laptop.   Will the linux partitions retain their original name or be transfered to sda1&2 or whatever?   Or, Install windows and leave enough unallocated space for  Ubuntu, then install wubi in the new win7 and copy the data from the old wubi install then do the transfer.   That may be the best under the circumstances.  What do you or someone else who is the wubi guru advise.
Thanks
Michael

---

### Post by oldfred on 2013-12-13
Ubuntu now uses UUID not devices like /dev/sda1, so it will boot even if device number changes. Sometimes some configuration in fstab or grub reinstall may be required.

Windows is the one that is very particular. It has to have a primary partition (sda1 thru sda4) to boot from. Windows 7 normally uses 2 of the 4 allowed primary partitions, so we usually install an extended partition (which is also a primary). And then in the extended partition we can have an unlimited number of logical partitions. Also best to have Window before the extended partition. Windows installs will overwrite the MBR and write a new partition table and often does not properly handle the extended/logical partitions. 

       [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[URL="https://help.ubuntu.com/community/WindowsDualBoot"]https://help.ubuntu.com/community/WindowsDualBoot
[/URL]
 Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

[URL="https://help.ubuntu.com/community/WindowsDualBoot"]
[/URL]

---

### Post by mmcl26554 on 2013-12-20
I have successfully reinstalled Win7 AND transferred Ubuntu 12.04 from a WUBI install to a traditional install, yea!   However, there are two remaining problems which I will enumerate here but I can post them individually if that is the recommended thing to do.
1.  There are entries I don't want or even care about in the Grub boot menu.    "Previous Linux" & Windows recovery.   I have been able to remove the Memtest and recovery but it is not easy for me to identify what to remove from the "default grub configuration.   So I need some help there

2.  I use KeePass for passwords in both Win7 and Ubuntu on the same machine.   Under WUBI I had the Ubuntu install of KeePass use the database in Win7.   This worked great as the Win7 install was always mounted.   Now I have to have Ubuntu mount the Win7 partition and that does work.   The problem is that KeePass starts before the mounting of the Win7 partition and can't find it's database.   If I start keePass manually then it finds the database as by them the Win7 partition is mounted.  How can I change the order of these two functions and get the win7 partition mounted before Keepass is started.   This isn't a big problem as starting keepass is just a click away on the docked icon, but it isn't as mindless as it was with WUBI.  So I'm looking for some advice here.
Michael

---

### Post by oldfred on 2013-12-20
If it is just old kernels, you can use synaptic to delete kernels. I like to keep one old one just in case.
If you really want to customize grub menu, you can also do that.

       Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

If old kernels & you have upgraded, they may not be listed in dpkg to delete. Then you have to use command line in /boot to houseclean.

      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

You should mount your NTFS partition in fstab. Then it will be always mounted. But I prefer to have separate NTFS data partition and only mount the Windows system partition as read only. The Linux NTFS driver exposes all the hidden files & folders which may let you then make mistakes. Windows normally hides those files & folders.

References:

 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Some more specifics:
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

      
 ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

---

