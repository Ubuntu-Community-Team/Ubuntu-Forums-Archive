---
title: "Issue with mounting new second hard drive added"
date: 2013-11-13
forum: Installation &amp; Upgrades
---

### Post by tornado_moore_03 on 2013-11-13
Having issues with using second hard drive that was added (not mounted)

First I'm a little new to using Ubuntu and have issues with a second HDD. I have added a second hard drive to a computer. It just needs to be one big partition since this will only be storing log files. I used GParted to create the partition which appears to have went ok. From the GUI desktop, when I double-click on the on the drive, it gives me a warning saying "Failed to mount "snortlog", not authorized. I need for this drive to be available after reboots since our local snort program can store logs on it. Thx in advance for any help given.



sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00078f9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   480157695   240077824   83  Linux
/dev/sda2       480159742   488280063     4060161    5  Extended
/dev/sda5       480159744   488280063     4060160   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004b547

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001   83  Linux

---

### Post by grahammechanical on 2013-11-13
Can you access that disk with File Manager? Check the permissions. Also if you have created folders on that disk, then check the permissions. Make sure that the program does not need to be Root to Create and Delete files.

Regards.

---

### Post by oldfred on 2013-11-13
Your file manager will try to automount it by label with defaults.
Better to add to fstab so it is auto mounted every time you reboot.
And you need to set ownership & permissions.
       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

      
 sudo fdisk -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

---

### Post by tornado_moore_03 on 2013-11-13
thx for the help. Got it working now.

---

