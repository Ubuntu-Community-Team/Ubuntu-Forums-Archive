---
title: "Dual boot with Windows 7"
date: 2019-06-03
forum: Installation &amp; Upgrades
---

### Post by pantelidisk on 2019-06-03
I installed ubuntu by mistake on a small usb drive of 16GB with dual boot on my Windows 7. It created automatically 2 partitions and the main partition of ubuntu is about 5Gb. It is too small even to complete even the first update.
It now has a boot loader that can only work with the flash drive on.
I made a partition of 50 GB on the main disk and I would like to use that one for ubuntu. How can I do it to install again ubuntu there, update the boot loader and completely uninstall the version that I have already?
I'm afraid to mess up with the boot loader and I'm new in ubuntu.

---

### Post by oldfred on 2019-06-03
UEFI or BIOS?
Most Windows 7 installs are BIOS with MBR partitioning. And then you have the old 4 primary partition limit.
Post this:
sudo parted -l

---

### Post by pantelidisk on 2019-06-03
It is BIOS. I do have 4 primary partitions as you said plus one on the USB. What should I do to install ubuntu on the 50GB partition with dual boot and get rid of the stick?

Model: ATA ST9500420AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  106MB  105MB   primary  ntfs         boot
 2      106MB   126GB  126GB   primary  ntfs
 3      126GB   450GB  324GB   primary  ntfs
 4      450GB   500GB  49,9GB  primary  ext4


Model:  USB Flash Memory (scsi)
Disk /dev/sdb: 15,5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      32,3kB  9664MB  9664MB  primary   fat32        boot, lba
 2      9665MB  15,5GB  5853MB  extended
 5      9665MB  15,5GB  5853MB  logical   ext4

---

### Post by oldfred on 2019-06-03
You just need to use Something Else to install. Then Select your sda4 partition, but check during install that still is sda4, some flash drives get promoted to sda on reboot. And on partitioning screen use change button to make sda4 as ext4 & use as /. Installs now use swap file, so no swap required. it should have sda as default in combo box at bottom of partitioning screen.

Also back up your Windows and make a Windows repair disk. Grub will normally boot Windows, but if Windows has issues, then grub will not boot it. And most fixes to Windows cannot be done from Ubuntu.

[https://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html](https://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html)

May show older screens but install is still the same.
       [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
16.04 install screens
[https://www.ubuntu.com/download/desktop/install-ubuntu-desktop](https://www.ubuntu.com/download/desktop/install-ubuntu-desktop)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu) 
    
Note Windows 7 will reach End of Life in 2020.

---

### Post by drv9977 on 2019-06-06
you may need to fresh install it on the same partition you want to install ubuntu.

---

### Post by pantelidisk on 2019-07-08
Hello,
I finally got a bigger flash disk and I want to use that one instead. But for some reason it is reading it as sdb1 and not sda4. I managed to change with the change button to ext4 but I can't switch it to sda4 since there is another partition with that name. Would that be an issue?

What should I do now? Should I just try the default first option to install it alongside Windows as I did the first time?

Thanks for your help

---

### Post by oldfred on 2019-07-08
With BIOS/MBR, you only have 4 primary partitions. If you have used all 4, you cannot install. 
You have to convert one primary to an extended partition which acts as a container for as many logical partitions as you want. Ubuntu installs just fine into a logical partition, Windows does not.

Note, older, but still valid for older BIOS/MBR configurations:
        My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
sudo Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
This suggests removing system partition and making c: the bootable partition. But has details on all alternatives
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019)
Shrinking a Windows Vista/7/8 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

