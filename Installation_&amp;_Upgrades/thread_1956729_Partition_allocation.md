---
title: "Partition allocation"
date: 2012-04-11
forum: Installation &amp; Upgrades
---

### Post by PhilJD on 2012-04-11
I am trying to install Ubuntu 10.10 in dual boot mode. When I installed it to a laptop the installer automatically created a partition for Ubuntu to be installed to. However, when I try to install to my desktop I only get the option to wipe the disk or manually allocated partition (which is described as advanced). Why won't it do this automatically for me? What can I do to complete a dual boot install?

---

### Post by darkod on 2012-04-11
There can be a number of reasons, but most probable is that you are using the maximum of 4 partitions on the disk. Since installing ubuntu means creating new partitions, it can't go over the limit of 4.

Another reason might be if there is an error in the partition table, which windows might ignore, but ubuntu not. Due to this error it can't read it correctly and offers only to wipe it all.

Boot with the cd first in live mode, open Terminal and post the output of:
sudo fdisk -l (small L)

---

### Post by PhilJD on 2012-04-12
Thanks for offering to help. It is much appreciated.

As far as I am aware, there is only one partition. I have tried to make the current partition smaller in order to ensure that is empty space on the drive for a new partition, but that didn't help.

I have entered the command you suggested and here is the result:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe02ae02a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          40        4279    34049770    7  HPFS/NTFS
ubuntu@ubuntu:~$

Thanks,

Phil.

---

### Post by PhilJD on 2012-04-16
I have tried changing the partitions but no success. Currently, I have one partition and some free space that I intended for the Ubuntu install.
 
[ATTACH]216125[/ATTACH]
 
[ATTACH]216126[/ATTACH]
 
I can select 'Specify partitions manually'- see first attachment - but what do I enter on the next screen - see second attachment - in order to complete an install that will allow me to dual boot with Windows and Ubuntu.
 
Thanks,
 
Phil.

---

### Post by darkod on 2012-04-16
First, the unallocated space of only 5GB is very small. Are you sure you want to try installing on only 5GB?

You can try install the manual way, but since it didn't detect windows it will not add an entry for it and won't be able to boot it anyway. So I suggest you first solve the problem of not detecting windows. You will have to anyway sooner or later.

Have you tried booting windows and executing something like:
chkdsk /r C:

Sometimes there is some corruption on the windows system partition and ubuntu is not reading it correctly. Running chkdsk from windows would repair any faults from that aspect. See if it helps.

---

### Post by PhilJD on 2012-04-17
I have tried chkdsk but it made no difference. 

Any other ideas for me to try?

Thanks,

Phil.

---

### Post by oldfred on 2012-04-17
How full is Windows partition? Windows likes 30% free to work really well. Not sure how small gparted will let you make it, but at 10% free Windows just about stops working.

Also chkdsk may need more than one run, if errors were found. It does not fix everything on one pass.

---

### Post by PhilJD on 2012-04-21
I have run chkdsk several times and it reports no errors. 
I have also created a disk for 11.10 and tried that. This says 'Windows XP is already installed on this computer" so clearly the installer has recognised windows but I still don't get the option to install Ubuntu alongside Windows. Just "replace" or "something else". 
Does anyone else any further suggestions?
Thanks,
Phil.

---

### Post by dino99 on 2012-04-21
here is how to install:


use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate will be used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

so that mean you need to make room on your windows partition by uninstalling what you dont need, erasing old things, defragmenting then shrinking it .

---

### Post by oldfred on 2012-04-21
The replace or something else is usually because you have used all 4 primary partitions. You then have to backup & delete one of those and make it the extended partition which can hold many logical partitions. Windows only boots from a primary partition, but Linux works just fine from logical partitions.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. fullcirclemagazine.org
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

