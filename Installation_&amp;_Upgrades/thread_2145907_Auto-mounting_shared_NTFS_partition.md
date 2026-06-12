---
title: "Auto-mounting shared NTFS partition"
date: 2013-05-16
forum: Installation &amp; Upgrades
---

### Post by chellrose on 2013-05-16
Recently upgraded to 12.04 and decided to try out Xubuntu.  (and by "upgrade", I mean "install the new OS from the live CD, simultaneously wiping out the old one.")  I had 3 (major) partitions: Win7, Linux, and a second NTFS partition accessible by both operating systems.  During the install, I added some free space to the shared partition and so I had to reformat that partition.  The installer's partition utility didn't have NTFS as an option, so I formatted the thing as FAT32 and then immediately went into Windows and reformatted it as NTFS.

During boot, I get an error message stating that the partition is not mounted or not yet ready.  I suspected that might have something to do with the reformatting, so I went into /etc/fstab and changed "fat32" to "ntfs" and rebooted.  No dice.  Is there something else I need to do?  Google wasn't helpful, and while I've been an Ubuntu user for years, I'm still fairly new at messing around with fstab and such.

Thanks!

Oh, and I can mount the partition manually with ```
udisks --mount /dev/sda7
``` which appears to mount the partition in /media/(some long string of characters).  I don't actually have anything *on* the partition yet.  It reads as 4.0K where it *should* be 41 GB, but I recall that directories always list as 4.0K, so I'm probably looking up the size incorrectly.  (I used du -hs)

---

### Post by oldfred on 2013-05-16
If it is NTFS and you resized it, you probably need to run chkdsk on it.

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

      
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

---

### Post by chellrose on 2013-05-17
Worked like a charm.  And I'm going to stash those links in a folder somewhere for future fstab reference.  Thanks! :-D

---

### Post by oldfred on 2013-05-17
Glad that worked. :)

If flash drives or any partition gets mounted with UUID (that long number), then it may be worthwhile to label your partitions. I prefer to label everything, but have labeled a partition Data and mounted it as /mnt/data and Data is not equal to data as Linux is case sensitive. So I have to keep track of if I have mounted myself or if system has mounted it, (more when booting another test install ).

---

