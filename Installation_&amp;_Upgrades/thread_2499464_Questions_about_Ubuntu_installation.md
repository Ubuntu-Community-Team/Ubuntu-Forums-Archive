---
title: "Questions about Ubuntu installation"
date: 2024-07-28
forum: Installation &amp; Upgrades
---

### Post by crashlanding on 2024-07-28
Hi, I just re-installed Ubuntu 20.04.6LTS. It created 3 partitions. The first is 998MB (12.1% full), mounted at /boot/efi This must be the OS, right ? 
The second partition is 8.6GB, not mounted. For partition type the second partition says Microsoft Reserved. What is this ?  Should I leave it alone ?
The third partition is 2TB for filesystem. 2.1% full, mounted at Filesystem Root.
The first two partitions say FAT (32-bit version). I thought Linux required the Ext4 file system, which the third partition has. Why is the OS installed on FAT 32-bit ?
Thank you for your help.

---

### Post by Dennis N on 2024-07-28
The FAT 32 partition mounted at /boot/efi is the EFI system partition (ESP), which contains the Ubuntu boot loader. Your OS is not on the ESP, it's installed on the 2 TB root partition.

The Microsoft Reserved partition was not created by the Ubuntu installer. It must have been there already. If you had used the "Erase Disk and Install Ubuntu" installation option, it would have been deleted.

---

### Post by ajgreeny on 2024-07-28
> **crashlanding said:**
> Hi, I just re-installed Ubuntu 20.04.6LTS. It created 3 partitions. The first is 998MB (12.1% full), mounted at /boot/efi This must be the OS, right ? 
The second partition is 8.6GB, not mounted. For partition type the second partition says Microsoft Reserved. What is this ?  Should I leave it alone ?
The third partition is 2TB for filesystem. 2.1% full, mounted at Filesystem Root.
The first two partitions say FAT (32-bit version). I thought Linux required the Ext4 file system, which the third partition has. Why is the OS installed on FAT 32-bit ?
Thank you for your help.
No, you have completely misunderstood what has happened during the installation and how your complete filesystem is arranged in all Linux distros.

The first partition of 998MB mounted at /boot/efi is your UEFI partition needed for the booting of your new OS which I assume you installed in UEFI mode.

I have no idea what the second partition of 8.6GB is though it may be a leftover from a previous Windows system. I have not used Windows for many years so I can't help much more about that; it will be interesting to investigate this further, and to hear other answers. See also my later request.

The final 2TB filesystem is your OS root partition in which all the subfolders of the OS are placed when you install the OS.

So we can know more about your system, and assuming you can boot and run it, please show the total output of terminal command ```
inxi -Fzx
``` which will show lots of detailed info
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by yancek on 2024-07-28
The second partition which shows Microsoft Reserved is useless if you do not have windows installed.

ext4 is the default filesystem type for Ubuntu and a number of other Linux systems but there are a number of other filesystem types available.

---

### Post by crashlanding on 2024-07-28
inxi - Fzx 
inxi: command not found

I bought this computer from Dell with Ubuntu 20.04.6LTS installed. I use it for writing Ubuntu programs using Embarcadero's RAD Studio. After several months a low filesystem memory message came. I  uninstalled Flightgear and other programs I had installed, and also Solitare and the other pre-installed games. I then re-booted. he computer worked for another 3 or 4 months and then showed the low filesystem memory alert again, and suggested I empty the trash. I emptied the trash, and rebooted, and it never booted again.

I re-installed 20.04.6LTS, still the latest version of Ubuntu compatible with Rad Studio. I used the first option which said it would erase everything. I used a USB for the installation. I don't know how much filesystem space was allocated when I received the computer. I wouldn't think programming would use up much space. 

The computer came with two 2-TB hard drives. I want to be sure everything is set up correctly and with lots of filesystem space before I continue. Since it didn't erase the WIndows folder, should I do another re-install with the second or third option ? For a week before this computer went low again I was getting some odd behavior from my program. Suddenly it could not find the setup file it always found, which was there. I struggled with that until I got the filesystem message the second time. 

Perhaps it is safer to re-install. The other thing is that I have a second 2-TB hard drive. It was partitioned, so I formatted it and can use it. But it might be best if it can add filesystem space. So, how would I set the root point so it adds space, /home ? I can send a copy of the data from Settings>About, Drives and df -h if that helps. Do I add them as a reply ?

---

### Post by ajgreeny on 2024-07-29
No don't reinstall yet as we still cannot see what is wrong and do not know your current partition layout on the two disks.

Boot to your live USB system and choose try Ubuntu without installing it.
From that live system run terminal command
**sudo fdisk -l** 
and show us the output of that using code tags (there is a how-to below).

Do you still have a Windows OS installed? The partitions you mentioned in your first post do not use all the disk space of even one of the two 2T disks you say you have, hence my suggestion of the fdisk command.

---

### Post by crashlanding on 2024-07-29
```

Disk /dev/loop0: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 45.95 MiB, 48160768 bytes, 94064 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 346.34 MiB, 363151360 bytes, 709280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 63.29 MiB, 66359296 bytes, 129608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 91.7 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 49.86 MiB, 52260864 bytes, 102072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 63.97 MiB, 67051520 bytes, 130960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 38.85 MiB, 40714240 bytes, 79520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 1.88 TiB, 2048408248320 bytes, 4000797360 sectors
Disk model: PC801 NVMe SK hynix 2TB                 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F81A2D5A-01DE-4208-8856-282575C8F0ED

Device           Start        End    Sectors  Size Type
/dev/nvme0n1p1    2048    1050623    1048576  512M EFI System
/dev/nvme0n1p2 1050624 4000796671 3999746048  1.9T Linux filesystem


Disk /dev/nvme1n1: 1.88 TiB, 2048408248320 bytes, 4000797360 sectors
Disk model: PC801 NVMe SK hynix 2TB                 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop8: 349.71 MiB, 366682112 bytes, 716176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```
Since re-installing Ubuntu it  boots and runs.So I was able to run fdisk from terminal without booting using the USB. What I am writing about is that since I had two computers fail after suddenly going filesystem memory low, I want to make sure everything is set up correctly in the new installation, so it doesn't happen again. This computer came from Dell with Ubuntu 20.04.6LTS. Dell must have placed the Windows folder as part of Linux, perhaps in case the buyer wants to install Windows side by side with Linux. I wish I knew how Dell had the filesystem partitioned when I got it, and why it ran out of filesystem memory. When I realized the new installation did not completely overwrite the old installation I worried about some trace of a corrupted filesystem remaining. So yesterday I re-installed 20.04.6LTS. It runs. The installation did not touch the second hard drive, which I had already formatted and rooted so it is available to me. The Windows folder is gone. I think everything else is okay and that I am ready to get set up again for programming. But I want to see if I can root the second drive so it adds to the filesystem space. Unless there is some other issue I don't know about yet, that is the last bit of information I need, how to root the second drive. Telling me quickly that the windows folder must have already been there helped me quite a bit. Thank you.,

---

### Post by Dennis N on 2024-07-29
>  I want to see if I can root the second drive so it adds to the filesystem space.

I'm not sure what you mean by "root the second drive", but you cannot span the OS root partition across two disks. What you can do is mount a partition on the second disk with mount point inside the OS root partition of the first disk in order to create more space for storing some of your data files. Many users do this, by mounting the additional partition at startup with an entry in /etc/fstab.

In the display of post #7, nvme1n1 does not show a partition table (Disklabel) yet. You need to create one and then add an ext4 partition for use by Linux.

---

### Post by Impavidus on 2024-07-30
> **crashlanding said:**
> 
I bought this computer from Dell with Ubuntu 20.04.6LTS installed. I use it for writing Ubuntu programs using Embarcadero's RAD Studio. After several months a low filesystem memory message came. I  uninstalled Flightgear and other programs I had installed, and also Solitare and the other pre-installed games. I then re-booted. he computer worked for another 3 or 4 months and then showed the low filesystem memory alert again, and suggested I empty the trash. I emptied the trash, and rebooted, and it never booted again. The Flightgear flight simulator can take a lot of disk space. I don't know whether removing the package also removes all add-ons (it didn't last time I used it, but that's a while ago and I need a new computer before trying Flightgear again). Those add-ons, in particular the scenery database, is what takes most of the disk space. The pre-installed games are tiny. I'm not familiar with RAD Studio. I program, but don't use any IDEs.

> I re-installed 20.04.6LTS, still the latest version of Ubuntu compatible with Rad Studio. I used the first option which said it would erase everything. I used a USB for the installation. I don't know how much filesystem space was allocated when I received the computer. I wouldn't think programming would use up much space.Programming doesn't take a lot of space, unless in a ridiculously bloated environment. But even then, 2TB seems excessive. Next time, investigate what uses all that disk space. Some common culprits: overflowing log files with repeating messages, backups sent to the same drive instead of a backup drive, obsessively collecting media files.

> Perhaps it is safer to re-install. The other thing is that I have a second 2-TB hard drive. It was partitioned, so I formatted it and can use it. But it might be best if it can add filesystem space. So, how would I set the root point so it adds space, /home ? I can send a copy of the data from Settings>About, Drives and df -h if that helps. Do I add them as a reply ?Many use a separate /home partition. It has some advantages if you want to keep your files when reinstalling your OS. If you have a separate /home partition, 2TB for the root partition is very large. But you mentioned Flightgear. IIRC, the data files for that, which can be very large, are normally stored in /usr/share/games/flightgear. It might be good to have them on one drive, your /home on the other. And then, it may also be a good idea to have /usr/share/games on a different partition than your OS.

> **crashlanding said:**
> The installation did not touch the second hard drive, which I had already formatted and rooted so it is available to me. The Windows folder is gone. I think everything else is okay and that I am ready to get set up again for programming. But I want to see if I can root the second drive so it adds to the filesystem space. Unless there is some other issue I don't know about yet, that is the last bit of information I need, how to root the second drive. Telling me quickly that the windows folder must have already been there helped me quite a bit. Thank you.,I'm not familiar with the verb "to root" in the context of filesystems. It may be some non-standard terminology you picked up somewhere. It happens to all of us. You can create a filesystem on it (easiest with gparted) and use /etc/fstab to configure your system to mount it somewhere.

There are tricks to merge multiple drives into one filesystem (using logical volume management), but that's not recommended. It's a more advanced skill and means that everything is lost as soon as one drive fails.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by crashlanding on 2024-07-30
When I say "root the second drive", I mean to set a mount point for it. The second drive appears when I click + other locations. There I find Computer, the first hard drive, and Disk2, the second hard drive. I found that Disk 2 was partitioned, but not formatted. So Dell delivered my computer with the second hard drive partitioned but not formatted. Now I know how to fix this. But I never guessed the second drive was delivered unusable. I will not put Flight gear onto this computer. I have another computer now with Flight Gear on it. I can use the space on the second hard drive as it is, but perhaps it would be better if I change it's mount point to /home. Programming with RAD Studio involves a Windows computer running RAD Studio, connected by a network cable to a Linux computer. I think most of the compile process happens on the Windows computer and then the compiled program is placed into a folder on the Linux computer and the program runs, on the Linux computer. I can compile and run on Windows by switching the target OS. I can compile for Android, the computer is connected to an Android device via USB. I could also compile for Apple and IOS if I had such a device connected to the Windows machine. Just though you might be interested.
When I click on Disk2, it shows an empty directory, and says "Folder is Empty". I think I should change the mount point for drive 2 to /home, because it will automatically be used. I don't really need to store files on the second drive as part of writing programs. The things I add to support programs include tiny sound files, and configuration files, and images for the desktop shortcuts. I put configuration files into the public directory. I put the program and images into a folder i create in home, MyPrograms, in separate folders for each program.
All I have done since re-installing Ubuntu, and formatting the second drive, is to do Ubuntu updates. I haven't installed any files. Can I simply change the mount point of the second drive to /home now ?
I formatted the existing partition on the second drive ext4, but did not create a partition table for it. I did give it a name Disk2. Wouldn't Ubuntu add the partition table when the partition is created ? Perhaps this drive was partitioned, but without a partition table. Maybe I need to go back and start over again ? Or else, how do I add a partition table ? I used Disks to format the existing partition on Disk2.

---

### Post by ubfan1 on 2024-07-30
While you can certainly format a disk without a partition table, that is not standard usage, and mounts then need the loop option (like a big file). The partition tools like gdisk have explicit commands to make a new partition table, actually several depending upon the type of partition table. Use the build in help command to see the command options (?, or m, or ...).  After the partition table is made, then add partitions, then format them (probably with another tool like mkfs).

---

### Post by yancek on 2024-07-30
You might be better off, since you have nothing on the second drive now, to create a partition table (GPT) and a partition or partitions and then format them.

>  I think I should change the mount point for drive 2 to /home, because it will automatically be used. 

No.  If you want to use the 2nd drive for /home you would need to create an appropriate entry in the /etc/fstab file and then move everything from your /home directory on the first drive to the /home partition on the second drive and would then always need the 2nd drive attached.  Better and simpler to just create a data partition on the second drive to store data files there.

---

### Post by crashlanding on 2024-08-10
!

---

### Post by crashlanding on 2024-08-10
Hi, I think I have just about got it all working. It has not been easy. First, I added a partition table. That made the partition become "Unallocated space". As unallocated space, I could not do anything with it, all options were grayed out. I read about unallocated space, but nothing seemed to help. Finally, I re-partitioned, formatted and added the partition table, a couple of times. Finally it looked right. It was no longer unallocated, and it became red, like a usable partition. So I set the mount point at /home, and set it to mount automatically at startup. I re-booted. Now after accepting my password, it kept asking for it again and again. I booted into the flash drive and reset the mount point to its default. I re-booted and again was in the password loop. I used the fllash again and unmounted the second drive. I was still in the password loop. I re-installed Ubnuntu and this time with the second drive already prepared, the second hard drive was automatically mounted. Now I see drive two in Other Locations. When I select it it says Folder is Empty. So I tried to copy a folder with pictures I use for the screen background, to the second hard drive. I get Error while copying. The folder cannot be copied because you do not have permission to create it in the destination. I tried to create a folder in the new drive by right clicking. But the New Folder option is gray, unavailable. The New Folder option in the drop down menu from the Drive2 thing in the upper left of the folder view, is also gray and unavailable. I right clicked in the directory area and selected properties (for the second drive). Under permissions, all three boxes are grayed out, and it tells me You are not the owner, so you cannot change these permissions. I looked this up on the internet and found that I need to use the chmod command. However, everything here is about not being able to access a file, not about accessing the hard drive. I don't know how to use chmod so it fixes the drive, or the partition. I have given up on the idea of mounting the second drive at /home. I will be happy just to be able to use the second drive. My guess is that the second drive needs to be set up before installing Ubuntu on the first hard drive. That must be why I got into the endless password loop. There were already folders in /home, so it was too late to set the second drive to /home.
Please tell me how to gain access to the second hard drive.

---

### Post by crashlanding on 2024-08-10
Here is the result I am currently getting from the df -h command in case it helps:
  	 	 	 	   Filesystem      Size  Used Avail Use% Mounted on
 udev             16G     0   16G   0% /dev
 tmpfs           3.2G  2.6M  3.2G   1% /run
 /dev/nvme0n1p2  1.9T  9.8G  1.8T   1% /
 tmpfs            16G     0   16G   0% /dev/shm
 tmpfs           5.0M  4.0K  5.0M   1% /run/lock
 tmpfs            16G     0   16G   0% /sys/fs/cgroup
 /dev/loop0      128K  128K     0 100% /snap/bare/5
 /dev/loop2       92M   92M     0 100% /snap/gtk-common-themes/1535
 /dev/loop3       46M   46M     0 100% /snap/snap-store/638
 /dev/loop1       64M   64M     0 100% /snap/core20/1828
 /dev/loop4      347M  347M     0 100% /snap/gnome-3-38-2004/119
 /dev/loop5       50M   50M     0 100% /snap/snapd/18357
 /dev/nvme0n1p1  511M   51M  461M  10% /boot/efi
 tmpfs           3.2G  108K  3.2G   1% /run/user/1000
 /dev/sda1       231G  1.8G  230G   1% /media/chris/USBFlash256
 /dev/nvme1n1p1  1.9T   28K  1.8T   1% /media/chris/Drive2
 /dev/loop6       39M   39M     0 100% /snap/snapd/21759
 /dev/loop7       64M   64M     0 100% /snap/core20/2318
 /dev/loop8      350M  350M     0 100% /snap/gnome-3-38-2004/143

---

