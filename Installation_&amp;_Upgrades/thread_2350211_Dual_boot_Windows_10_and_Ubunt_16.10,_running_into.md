---
title: "Dual boot Windows 10 and Ubunt 16.10, running into issues with partitioning"
date: 2017-01-22
forum: Installation &amp; Upgrades
---

### Post by aewhatley on 2017-01-22
Also posted on askubuntu: ([http://askubuntu.com/questions/874811/can-no-longer-resize-c-drive-partition?noredirect=1#comment1358675_874811](http://askubuntu.com/questions/874811/can-no-longer-resize-c-drive-partition?noredirect=1#comment1358675_874811)). 

I had a dual boot setup between Ubuntu 16.10 and Windows 10, but then I deleted the Ubuntu partition and merged it back into the windows partition. However, I am now unable to manually create the Ubuntu partition when dual booting as I was able to before (using the sliding bar tool), as it appears that Ubuntu cannot recognize the partition and the amount of space on it. I've read in other posts that this could be due to the Windows partition using a dynamic disk, but based on diagnostics, it looks like my partition uses GPT. 

The outputs of the usual diagnostic commands are here. I have also included a screenshot of the Gparted window in a live session. Notice how Ubuntu is unable to recognize how much used space there is on the Windows partition. Any help would be appreciated. Thank you. 

[https://i.stack.imgur.com/qX6f5.png](https://i.stack.imgur.com/qX6f5.png)

ubuntu@ubuntu:~$```
 sudo lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sdb      8:16   1  29.8G  0 disk 
&#9492;&#9472;sdb1   8:17   1  29.8G  0 part /cdrom
sr0     11:0    1  1024M  0 rom  
loop0    7:0    0   1.4G  1 loop /rofs
sda      8:0    0 931.5G  0 disk 
&#9500;&#9472;sda4   8:4    0 902.2G  0 part 
&#9500;&#9472;sda2   8:2    0   260M  0 part 
&#9500;&#9472;sda7   8:7    0    27G  0 part 
&#9500;&#9472;sda5   8:5    0   875M  0 part 
&#9500;&#9472;sda3   8:3    0   128M  0 part 
&#9500;&#9472;sda1   8:1    0   650M  0 part 
&#9492;&#9472;sda6   8:6    0   450M  0 part 
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda
Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: BD29FBA9-B2D7-4727-A310-46279AA7A753

Device          Start        End    Sectors   Size Type
/dev/sda1        2048    1333247    1331200   650M Windows recovery environment
/dev/sda2     1333248    1865727     532480   260M EFI System
/dev/sda3     1865728    2127871     262144   128M Microsoft reserved
/dev/sda4     2127872 1894123736 1891995865 902.2G Microsoft basic data
/dev/sda5  1894127616 1895919615    1792000   875M Windows recovery environment
/dev/sda6  1895919616 1896841215     921600   450M Windows recovery environment
/dev/sda7  1896841216 1953513471   56672256    27G Microsoft basic data

ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  683MB   682MB   ntfs         Basic data partition          hidden, diag
 2      683MB   955MB   273MB   fat32        EFI system partition          boot, esp
 3      955MB   1089MB  134MB                Microsoft reserved partition  msftres
 4      1089MB  970GB   969GB   ntfs         Basic data partition          msftdata
 5      970GB   971GB   918MB   ntfs                                       hidden, diag
 6      971GB   971GB   472MB   ntfs                                       hidden, diag
 7      971GB   1000GB  29.0GB  ntfs         Basic data partition          hidden, msftdata
```

---

### Post by oldfred on 2017-01-22
The red icon is standard on Microsofts system reserved partition.

But you should not have red icon on Windows main partition.
When you try to mount it it gives warning that is is RAID, needs chkdsk, or is hibernated.

Usually the problem is hibernation, but if just resized it may need chkdsk.
Turn off fast start up in Windows. Windows on updates may also turn it back on, so if issues later first thing to check.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by aewhatley on 2017-01-22
I ran chkdsk and there were no errors found. I'll try to disable fast start up, but I had fast start up on before when I dual booted Ubuntu, so this seems strange....

---

### Post by wildmanne39 on 2017-01-22
Please use thumbnails or url's when posting images because many people have slow or limited connections.

---

### Post by aewhatley on 2017-01-22
Ok, disabling fast startup appears to have done the trick. The grub menu is now not showing up, but that's a question for a different thread. Thanks for your help.

---

