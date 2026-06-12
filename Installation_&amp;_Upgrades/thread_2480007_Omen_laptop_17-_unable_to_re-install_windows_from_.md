---
title: "Omen laptop 17- unable to re-install windows from ubuntu 22.04"
date: 2022-10-15
forum: Installation &amp; Upgrades
---

### Post by ianadds2 on 2022-10-15
Hi,
  I recently purchased an Omen 17 laptop (details below) and installed Ubuntu 22.04 due to freeze up issues i was advised to return back to windows and see if the issue persisted. When i install windows via USB stick created on another computer using windows creation tool it starts the process of installation (end user agreement, language, then it searches for drives but none showing. I downloaded some drives and two show up in the box along with my HD partitions showing 1 of 2  512 mb and below 2 of 2 953 Gigs, and asks where do i want to install windows. 
This is where the issue is ,below it states i can't be installed because windows needs to be installed on a NTFS partition??

I am at a loss each way i go another issue comes up, so i need on the easiest way to get windows back , How do i reformat the current partition to NTFS i am not worried about files as it is backed up, i have tried different recovery ways to no avail. Please remember i am a Newbie so simple language would be great.


Omen 17, i T HD, 16 gigs of ram, 6 gigs memory intel core i7,Navidia G force RTX gaming laptop. Windows 8

PS: i Accept i was a real hasty in removing the windows side but i my defence ive been using LInux for quite a while and love it?

---

### Post by yancek on 2022-10-16
I would expect the windows installer to give you an option to create partitions and format them.  Do you not see that option?  It's been a long time since I've installed windows.
Boot the Ubuntu usb you used to install Ubuntu and select the Try Ubuntu option and open a terminal and enter:  sudo gparted   GParted is a gui front end for the parted partition manager and you can use it to create partitions and format them with various filesystems including ntfs.  This should work.

I don't understand how many partitions you have?  Is Ubuntu installed in UEFI mode?  It should be as if your drive is GPT, you will need to install windows UEFI.
You might post the output of the two commands below here so we can see what your drive(s) and partitions look like.

```
 sudo parted -l
 sudo fdisk -l
```

---

### Post by ianadds2 on 2022-10-16
Hi Yancek,
                 Thanks for your reply, The installer Displays the box but would only allow me to format the smaller partition of 512 but i expected when i pressed format that another box would show, unfortunately no box displayed.  Two partitions were displayed 1 of 2   512mb   and 2 of 2 953 Gigs and yes it was installed in UEFI mode.  When i install windows no drivers were displayed so i downloaded packages of drives and the two drives showed on the windows screen so was able to move onto the next stage but i cant go anywhere as it states the partitions should be  NTFS.

When i run Gparted on the area when you select type of partition it does not show NTFS only  ext 1,2,3,4 fat32,  I will try your option of  trying the ubuntu installer and seeing what options there are available.

Model: SAMSUNG MZVL21T0HCLR-00BH1 (nvme)
Disk /dev/nvme0n1: 1024GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   1024GB  1024GB  ext4




Disk /dev/nvme0n1: 953.87 GiB, 1024209543168 bytes, 2000409264 sectors
Disk model: SAMSUNG MZVL21T0HCLR-00BH1              
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A6F5EB42-87AD-4D65-80EB-3D7FA634F39E


Device           Start        End    Sectors   Size Type
/dev/nvme0n1p1    2048    1050623    1048576   512M EFI System
/dev/nvme0n1p2 1050624 2000408575 1999357952 953.4G Linux filesystem

---

### Post by ianadds2 on 2022-10-17
Hi Yancek
             Just to let you know i have been able to install windows and ubuntu as a dual boot, your advice was very helpful so thanks allot much appreciated.

Ian

---

