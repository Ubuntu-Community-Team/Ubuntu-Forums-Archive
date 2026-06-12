---
title: "Help with partitioning - avoiding data loss"
date: 2016-11-09
forum: Installation &amp; Upgrades
---

### Post by thatsmyboy on 2016-11-09
[ATTACH=CONFIG]272049[/ATTACH]I would like to be able to dual boot Ubuntu 16.04 LTS with (a currently broken) Windows. My original idea was to resize the Windows partition and move my data from one drive to another in the resulting space, then Install Ubuntu fresh on the original partition keeping the Windows data safely backed up on the same physical disk. Unfortunately, all the primary partitions are used, requiring me to remove one before recreating an extended partition - resulting in data loss. [IMG]http://imgur.com/8PO01sJ[/IMG] [IMG]http://imgur.com/xKDNGbA[/IMG] The real problem here is that I have about 100GB of pictures, videos, and documents that I would like to save without any 100GB removable medium to store it all on. Also windows is broken. Any ideas would be helpful!
 -tmb

---

### Post by oldfred on 2016-11-09
Best to fix Windows first.
While gparted can resize a NTFS partition, a few have had issues. So we always suggest using Windows own tools to resize NTFS and then reboot as after any change in size NTFS needs to run chkdsk. 
If you resize a broken Windows you may make it so it cannot be fixed.

If Windows 8 or later, you also have to make sure the fast start up or always on hibernation is off.

Many with HP remove the HP tools. Someone said those could easily be downloaded from HP again. Or use partitioning tools to change the HP tools partition to logical, shrink the NTFS, move unallocated into extended partition so then you can make more logical partitions for Ubuntu & swap.
       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by thatsmyboy on 2016-11-09
Thanks for the quick response! I will give those a try! I agree that Windows is better to fix first, but my primary aim was to save the data, I could really do without windows, but the partitioning was problematic. I'll let you know how it goes.

---

### Post by oldfred on 2016-11-09
You should be able to mount the Windows partition from the live installer, no need to install.
If NTFS is corrupted the Linux NTFS driver will not automount as it does read/write mount by default.
But you often still can mount read only.

       Read only mount of Windows may work if corrupted or hibernated use sda1, sda2 etc for sda#, whichever partition is your main Windows install. Often sda2.
sudo mkdir /mnt/win
sudo mount -o ro /dev/sda# /mnt/win
gksudo nautilus /mnt/win 

gksudo now not normally installed. Using graphical file browser with root privileges can be dangerous, so do not delete anything. And only use to copy files in read only Windows partition.

---

### Post by thatsmyboy on 2016-12-19
Okay, I was able to back up and retrieve most of what I needed from the computer. 
I followed the instructions at the link above, but for the run down here is what I did:
[LIST=1]
[*]move files from (primary) partitions 3 and 4 to folders I created on partition 2.
[*]delete partitions 3 and 4 with gparted on an ubuntu live cd (16.04 is the one I used)
[*]resize partition 2 to give some extra space for an extended partition. This step could have been omitted but I needed the space for large files. Remember, Windows installation was broken, but files were intact. 
[*]create an extended partition with similar structure (partition 3 with 3 logical partitions (5, 6, & 7))
[*] - it turns out that the restore partition didn't work in this configuration - i happened to have a copy of Windows that I installed fresh to overwrite the original install
[*]I am now trying to copy the files back to the Recovery and HP_TOOLS partitions
[/LIST]
[ATTACH=CONFIG]272773[/ATTACH]
I now just need to finish re-partitioning and move files as needed. The problem I have now is that the drive I need (Recovery the primary 3 partition on the hard drive ie sda3) is not showing up to be mounted. it shows in gparted. any further suggestions??

---

### Post by oldfred on 2016-12-19
Some with HP have posted that HP tools can be downloaded from HP site. But do not think they offer recovery partition. It always has been best to use it to create your own recovery and fully backup the installed copy of Windows as you may have made lots of changes & added lots of programs. If paid programs you must document serial numbers so you can re-install if needed.

---

