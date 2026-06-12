---
title: "NTFS-config tool won't let me in!"
date: 2013-10-06
forum: Installation &amp; Upgrades
---

### Post by ButchMel on 2013-10-06
I just installed 12.04.3 server with desktop GUI. Then installed the NTFS configuration tool with terminal. 

First: I was reading somewhere that NTFS now come ''out of the box'' in 12.04 and there's no need to use NTFS config tool - is that correct? (I need full access to these drives - this is a file server... from Macs and Windows machines in the place.)

Second: assuming I need such a tool (as I used it under 10.04 until 2 days ago), I have a major issue: when trying to launch it from the Dash Home where I can see it, it peompts me to enter my administrative password...but does not recognize it and kick me out after 3 trials.  I currently only have one single password on this system, so there's no other password it could confuse with.

Thanks,
B

**EDIT / UPDATE**:  I also have same issue with Samba ! ... Now that I found way to install graphic interface on it too (Note: I have not used it yet either even in terminal mode)

---

### Post by oldfred on 2013-10-06
Almost all the gui tools for configuring mounting of partitions have not been well maintained. You should just manually edit fstab. Old tools still use device and do not have correct parameters.
NTFS driver is included with Ubuntu.
You do have to have a working password as sudo or gksudo is often required.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
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

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

---

