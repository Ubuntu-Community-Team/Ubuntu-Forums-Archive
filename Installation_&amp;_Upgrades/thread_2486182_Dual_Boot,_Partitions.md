---
title: "Dual Boot, Partitions"
date: 2023-04-21
forum: Installation &amp; Upgrades
---

### Post by webmanoffesto on 2023-04-21
I have a Windows 11 laptop. I want it to dual boot Ubuntu. So I shrunk one partition by 30 GB and I labelled that partition as "/" root. Then I installed Ubuntu to that. I didn't create a Home directory. My thinking was that the 900GB partition will effectively be the Home. 
The main large partition has about 900GB and I want that to be where the files I use on a daily basis are, and I want to access that from Windows and Ubuntu. 
What it looks like now, is, I guess the Home directory is in the same 30 GB where the Root directory is. Inside the Root directory is a folder named Home.
And the 900GB partition was unmounted. I managed to mount it, and to navigate there in my file browser, but it is a bit awkward.
How can I get this working in a more natural manner. If I make the 900GB partition my Home partition, will that cause problems in Windows? (It is empty now, I'm not worried about losing files.)

---

### Post by oldfred on 2023-04-21
Back when I had XP, I had a shared NTFS partition and a Linux data partition. My /home then was tiny as it only had the user configuration files, mostly hidden. Thunderbird & Firefox were larger but also moved & shared.
But Windows 8 and later has made it a bit more difficult as it wants to use fast start up which sets hibernation flag. And it will turn it back on with some updates. You have to make sure hibernation flag is always off.

I use links. Some special cases may have issues, but I never have had any. Perhaps snaps may not like links.
[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

Another alternative.
/home/$USER/.config called user-dirs.dirs 
[https://askubuntu.com/questions/1271486/installing-ubuntu-on-ssd-and-setting-home-on-hdd](https://askubuntu.com/questions/1271486/installing-ubuntu-on-ssd-and-setting-home-on-hdd)

Your 30GB is not particularly large.
I have seen a few installs where snaps take 20GB by themselves. 
I use Kubuntu which is smaller and do not allow any snaps. And have used about 16GB of my 40GB / partition.

---

### Post by grahammechanical on 2023-04-22
Can Windows read Linux partitions? Not according to the information I have seen on this forum over the years. If you want to share a partition between Windows and a Linux distribution then I think you need to format the partition with a Windows format and not a Linux format. Ubuntu can read Windows NTFS partitions.

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Regards

---

### Post by webmanoffesto on 2023-04-22
Yes, I guess it's the Windows / Ubuntu shared partition which is complicating things. So maybe I should make the 900GB partition a NTFS partition and make that Ubuntu's Home partition. Would that work?

---

### Post by oldfred on 2023-04-22
Linux system partitions must be Linux formats like ext4. If putting all data in the NTFS partition you probably do not need separate /home.

As long as you keep fast start up off in Windows the Linux NTFS drive will allow you to mount as read/write. If other repairs like chkdsk are needed you can only do that from Windows & that can also cause issues.

Best to always have a Windows repair/recovery flash drive and Ubuntu live installer flash drive to make repairs. And good regular backups.

---

### Post by Impavidus on 2023-04-23
You can't make the NTFS partition your home partition. For some of your files (like some config files), the permissions and ownership matter, so your home directory must be on a Linux filesystem.

You can put an entry in your /etc/fstab to mount the NTFS partition automatically at boot and you can replace the Documents or Pictures directories in your home directory with symlinks to directories on the NTFS partition.

---

### Post by webmanoffesto on 2023-04-25
Here is my current partitioning
GParted Data, sda,

[LIST]
[*]Partition: /dev/sda1, Name: efi system partition, File System: fat32, Mount Point: /boot/efi, Label: System, Size: 260MiB, Flags: boot, esp
[*]Partition: /dev/sda2, Name: Microsoft reserved partition, File System: unkown, Mount Point: blank, Label: System, Size: 16+MiB, Flags: msftres
[*]Partition: /dev/sda3, Name: Basic data partition: File System: ntfs, Mount Point: /media/tom/Windows, Label: Windows, Size: 901GB, Flags: msftdata
[*]Partition:/dev/sda4, Name: Basic data partition: File System: ext4, Mount Point: /, /var/snap/firefox/common/host-hunspell, Label: blank, Size: 12.8GB, Flags: msftdata
[*]Partition: /dev/sda5, Name: blank: File System: ntfs, Mount Point: blank, Label: blank, Size: 838MiB, Flags: hidden, diag
[/LIST]
 
Would you recommend that I add a partition for an Ubuntu Home partition and keep the big NTFS partion? Is there a recommended partition size for Ubuntu Home when most files will be kept in the NTFS partition?

Is sda5 a hidden Windows recovery partition? Meaning is that the partition I would use to reinstall / recover the Windows installation if it stops working?

---

### Post by oldfred on 2023-04-25
Windows & vendor often have multiple backup/recovery partitions. I would not normally change any of them other than shrink with Windows tools to make room for Linux partitions.

My /home is 1.5GB. So I keep in in /. 
I have all data in a Linux data partition, and no snaps or games.
Firefox & Thunderbird are hidden folders in /home and can get larger. I used to share both across versions and it was not particular if Firefox version was not quite the same. Now it is very particular & I have to copy it, so now is back into default /home/.mozilla folder.

---

### Post by webmanoffesto on 2023-04-25
Would the below correctly mount my NTFS partition when I boot Ubuntu
Do I need the entire UUID 69bb6a6b-ee06-43eb-b22e-ae12a22e3c30

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=1d40de05-713a-46dc-afc5-5cf53a554987 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=C2D0-2772  /boot/efi       vfat    umask=0077      0       1

UUID=69bb6a6b-ee06-43eb-b22e-ae12a22e3c30 /media/ntfs ntfs rw,nosuid,nodev,noatime,allow_other 0 0

---

### Post by oldfred on 2023-04-25
You have to make the /media/ntfs mount point.

I have seen a variety of suggest parameters.

A couple;
nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,fstype=ntfs,uid=1000,gid=1000,fmask=0113,dmask=0022
nodev,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0113,dmask=0022
The big_writes mount option does help performance greatly.
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

There are even more if external drive or remote access.

---

### Post by webmanoffesto on 2023-04-25
Okay, I'm testing this.

I added "UUID=69bb6a6b-ee06-43eb-b22e-ae12a22e3c30 /media/ntfs ntfs nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,fstype=ntfs,uid=1000,gid=1000,fmask=0113,dmask=0022" to /etc/fstab
I saved the file.
Then in command line I typed:  $ sudo mount /media/ntfs
I get the error message:
mount: /media/ntfs: can't find UUID=69bb6a6b-ee06-43eb-b22e-ae12a22e3c30

What do you think the problem is?

---

### Post by oldfred on 2023-04-25
Does UUID match?
sudo lsblk -f

If added to fstab, you remount everything with this, if not errors then it mounted ok.
sudo mount -a
see also 
man mount

---

