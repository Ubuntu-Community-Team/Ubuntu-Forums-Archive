---
title: "Adding an Additional HDD"
date: 2012-11-10
forum: Installation &amp; Upgrades
---

### Post by Static1961 on 2012-11-10
I've got a new HP N40L that I'm wanting to use as a media server for Apple TV.

I've loaded Ubuntu 12.10 after giving up on trying to use Ubuntu server. When I set it up I had just one small drive in for the OS. I'm now wanting to add the 4 extra drives. I've started with one additional. I can see it via Dash Home / Disks but I don't know how to mount it for use.

I'm a complete novice on this stuff ... and whilst a number of (IT) people at work have said I should use Ubuntu I really struggling and thinking maybe I should just use Windows Home Server 2011. The other computers in our home are Mac's and Windows.

Thanks

---

### Post by drdos2006 on 2012-11-10
Once you have connected all the power and data cables, the disks need to be formatted. When the disks are formatted with ext3 or ext4 filesystem, then the disks recieve a Unique ID number ( for instance  UUID=74ab1607-3998-4265-81b3-6cc936af422d ).

To mount each drive /etc/fstab needs to edited as root.
( for instance "sudo gedit /etc/fstab" )
Make a backup first. ( "sudo cp /etc/fstab   /etc/fstab.backup" )

From a terminal, type "ls -l /dev/disk/by-uuid" to get the UUID of the drive. Highlight the UUID number, edit and paste the number into /etc/fstab. ( for instance, ## /dev/sdb1
UUID=74ab1607-3998-4265-81b3-6cc936af422d 	/media/sdb1	ext3	defaults	0	1

Save and close /etc/fstab.  From the terminal type "sudo mkdir  /media/sdb1" for the first drive, then mount the drive with "sudo mount -a".

Same for the other drives.

regards

---

### Post by Static1961 on 2012-11-10
How do I do it from the desktop ... not the terminal ?

(as it happens I'm in Manly ... Brisbane)

---

### Post by wildmanne39 on 2012-11-10
*Thread moved to **Installation & Upgrades**.*

---

### Post by oldfred on 2012-11-11
While there are several gui tools for automating the editing of fstab, they have not been maintained and often create more issues than they solve.

You should only need to copy & paste a few lines, edit UUID (more copy & paste) and assign names to the partitions as  mount points.

Pretty much the same as drdos2006's directions:
from Morbius1-----------------------------------------------------
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

---

