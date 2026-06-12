---
title: "have certain parts installed on separate drive?"
date: 2013-06-15
forum: Installation &amp; Upgrades
---

### Post by Drew U on 2013-06-15
I recently got my self 2 SSD's to place my OS's on and successfully installed Ubuntu on one and Windows 7 on the other. with my Windows I have the OS installed on the SSD and I am installing all programs on a 1TB HDD execpt for programs specifically needed to be with the OS. I want to do the same with Ubuntu.

I also want to make it so I can hide my Windows, System reserved(win) and 1tb windows programs file drive from Ubuntu so I or anyone else does not accidentally delete anything off it. (it be better if they need root password to access for use of trouble shooting)

---

### Post by Bucky Ball on 2013-06-15
Choose 'Something Else' at the partitioning section of the install, make your / partition for Ubuntu (20GB plenty), create a /home partition on another disk. You end up with you OS in / and your personal info on another disk in /home. (If you go this way don't forget a 2Gb /swap.)

As for the second bit, can't help, sorry. All I could think is that you set up users and groups and set permissions for what they can and can't do and access. Not sure if you can set a whole drive/partition but you can probably set directories.

---

### Post by 2F4U on 2013-06-15
I would think that you can prevent access to Windows partitions by adding appropriate mount options to /etc/fstab. Either prevent automatical mounting or mount read-only.

[http://ubuntuforums.org/showthread.php?t=1757405](http://ubuntuforums.org/showthread.php?t=1757405)
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by Bucky Ball on 2013-06-15
As suggested by 2F4U. A simple way might be in /etc/fstab add # and a space before the UUID for the NTFS partitions:

```
#Entry for /dev/sda* :
# UUID=6B8E2F2A62CEE191   /Your/Data     ntfs-3g defaults,locale=en_AU.UTF-8     0       0
```

The UUID will be your in your fstab and it will be pointing to the right mount point.

---

### Post by Mark Phelps on 2013-06-15
If the suggestions so far don't work, you can force the Windows partitions to mount read-ony (by adding "ro" to the fstab mount parms).  At least then, no one can accidentally write to the partitions.

---

### Post by oldfred on 2013-06-15
How large is your Ubuntu SSD?
I have a 60GB SSD and have two / (root) partitions, one for current install and the other for testing or next install. I use about 10GB of the 28GB available for my working install.
But I have all data on my hard drives and linked back in. 

My goal is that every drive should be fully bootable if any other drive fails (it may give mount errors on data but still will boot). If you have parts of essential system on different drives any drive failure will prevent boot.

---

### Post by Drew U on 2013-06-16
Ok, a couple things first off is there a way to mount /home and other parts to the one drive post install?

also I took a look at my /ect/fstab I'm not seeing any other drives other than ubuntu and swap?

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b9d90456-3ed4-4478-8296-9344472d7cb8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=9b61ed22-a872-4cc3-828e-3fb5a1cf4ae2 none            swap    sw              0       0
```

so I want to hide the windows drives from the folder system. 

one thing I think I forget to mention is that I want my one drive (3tb Media) to be mounted automatically, as I said I store all my media on it and want to link it to use in Ubuntu (music to banshee and xbmc, videos to xbmc ext)

---

### Post by oldfred on 2013-06-16
If you use Nautitus it will mount with label or UUID and with defaults. You need to create a mount point, set ownership & permissions and mount with fstab. Use template and change UUID & whatever name you want for mount point.

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

   For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

   ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if prevously mounted:
sudo mount -a

   Hide mount 
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0

   sudo mkdir /mnt/SysRes

   Set windows boot partition Read only - Morbius1
[http://ubuntuforums.org/showthread.php?t=2043862](http://ubuntuforums.org/showthread.php?t=2043862):
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=227 0 0 
UUID=xxxxxxxxxxxxxxx /WinC ntfs defaults,noauto,ro,umask=227 0 0

   Mount in /media or /home will show in Nautilus left panel mounts in / or /mnt will not.

 #If you cannot read and write then change the permissions. Not for NTFS
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
# 777 is read, write & execute by everyone
I recently learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX /mnt/data 
#is better than this:
sudo chmod 775 /mnt/data
sudo chown $USER:$USER /mnt/data
#where $USER should be your login name
#or to see user
echo $USER

---

### Post by Drew U on 2013-06-17
> **oldfred said:**
> If you use Nautitus it will mount with label or UUID and with defaults. You need to create a mount point, set ownership & permissions and mount with fstab. Use template and change UUID & whatever name you want for mount point.

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

   For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

   ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if prevously mounted:
sudo mount -a

   Hide mount 
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0

   sudo mkdir /mnt/SysRes

   Set windows boot partition Read only - Morbius1
[http://ubuntuforums.org/showthread.php?t=2043862](http://ubuntuforums.org/showthread.php?t=2043862):
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=227 0 0 
UUID=xxxxxxxxxxxxxxx /WinC ntfs defaults,noauto,ro,umask=227 0 0

   Mount in /media or /home will show in Nautilus left panel mounts in / or /mnt will not.

 #If you cannot read and write then change the permissions. Not for NTFS
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
# 777 is read, write & execute by everyone
I recently learned something - see post #8 & 10 by morbius1. Seems like a better way as you have more control over what is executable.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX /mnt/data 
#is better than this:
sudo chmod 775 /mnt/data
sudo chown $USER:$USER /mnt/data
#where $USER should be your login name
#or to see user
echo $USER

Yes this is great it hides the windows drives nicely, need to tweak it a little to get it just right but this helped a lot thank you!

One last thing, what do I need to put to make my other 3tb media NTFS drive mount automatically on start. (I am guessing to put "auto" where you had "noauto" when doing it for this drive)?

Marking this as solved too thanks.

---

### Post by oldfred on 2013-06-17
My post showed several examples, this was the standard. But use your UUID and change /media/WindD to your mount point. I prefer to mount in /mnt/data and link folders back into my /home.

 For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0

---

