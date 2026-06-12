---
title: "Help Installing Ubuntu 12.04"
date: 2012-10-24
forum: Installation &amp; Upgrades
---

### Post by Ymurti on 2012-10-24
Please help me!  I am trying to install Ubuntu in a netbook Eee PC that has windows 7 on it. I am using a cd. when I try to install I get this message "No root file system defined. Please correct this from the  partitioning menu."

Any help?

---

### Post by NikTh on 2012-10-24
Hi , 

are you using the "Something Else" option ? (in the installer window) 

Why you are not using the automate option "Install alongside Windows" ? 

Thanks

---

### Post by dolphin194 on 2012-10-24
You should choose "Install Ubuntu alongside Windows."

---

### Post by Bucky Ball on 2012-10-24
[I]Thread moved to [B]Installation & Upgrades


[/B][/I]Please try and give a bit more information, like if you want to keep Windows and whether you are using the 32 or 64bit version. Do you have the free space setup to install to? [I]

@ NikTh & dolphin194: [/I]Bit premature as the OP hasn't given much info and may have specific reasons for not doing an automatic install. And there are many ... The question is about the error message at boot, OP is possibly not even getting to the partitioning section ...

---

### Post by Ymurti on 2012-10-24
Thank You for your reply, here it is more details:

I want to install Ubuntu alongside with Windows.

I put the Ubuntu Cd in the computer, turn it on and after a while comes the welcome message with the options, Try Ubuntu or Install Ubuntu. I chose Install Ubuntu.
After have chosen if I want to connect to the Internet comes a screen with 3 options: 

- Install Ubuntu inside Windows 7

- Replace Windows 7 with Ubuntu

- Something else

Obs.: Does not have the option, "Install alongside Windows"

If I choose "Install Ubuntu inside Windows" then the process ends and I am asked to take out the CD and to press enter. After that Windows starts and of course Ubuntu is not there. 

If I choose Something else, comes Installation type and my partitions are there sda1, sda2, sda3 and sda4 and there are the options:  Quit, Back and Install Now. If I chose Install now comes "No root file system defined. Please correct this from the partitioning menu." Then I do not know what to do.

Please help!

---

### Post by Bucky Ball on 2012-10-24
Yea, you need to set up the partitions if you choose 'Something else'. That is why you are getting the error. You haven't set the root partition.

Follow this:

Make sure you have the free space to install Ubuntu to ready to go.
Choose 'something else' and create an extended partition using all your free space.
Now, create these three partitions inside the extended partitions by creating logical drives in there:

/ = root partition, the one the install is complaining about. The OS goes here. 15Gb should be plenty;
/home = where all your data will go, documents, vids, etc. There are other ways of going about this but this is a start. Make this as big as you like. Remember, your Win partitions, NTFS or FAT, will be accessible from Ubuntu also but not the other way around;
/swap = 2Gb fine.

The mount point names are all defaults in there so you just need to choose them. You should end up with an extended partition with three logical drives inside it. All good. There are a million howtos on dual-booting out there. Here's one I recommend:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

More questions just ask but that's your problem ... 'Something Else' is not an automatic install, it's manual and you need to set things up, including your / partition.

PS: Your other issue could be you don't have any free space or you already have four primary partitions on it. That is the maximum. Thus, three primary and an extended partition, inside which you can have as many logical drives as your hardware can handle ...

---

### Post by Ymurti on 2012-10-24
> **Bucky Ball said:**
> Yea, you need to set up the partitions if you choose 'Something else'. That is why you are getting the error. You haven't set the root partition.

Follow this:

Make sure you have the free space to install Ubuntu to ready to go.
Choose 'something else' and create an extended partition using all your free space.
Now, create these three partitions inside the extended partitions by creating logical drives in there:

/ = root partition, the one the install is complaining about. The OS goes here. 15Gb should be plenty;
/home = where all your data will go, documents, vids, etc. There are other ways of going about this but this is a start. Make this as big as you like. Remember, your Win partitions, NTFS or FAT, will be accessible from Ubuntu also but not the other way around;
/swap = 2Gb fine.

The mount point names are all defaults in there so you just need to choose them. You should end up with an extended partition with three logical drives inside it. All good. There are a million howtos on dual-booting out there. Here's one I recommend:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

More questions just ask but that's your problem ... 'Something Else' is not an automatic install, it's manual and you need to set things up, including your / partition.

PS: Your other issue could be you don't have any free space or you already have four primary partitions on it. That is the maximum. Thus, three primary and an extended partition, inside which you can have as many logical drives as your hardware can handle ...
Dear Bucky,  

I have chosen something else and then I have this options:
New Partition Table, Add, Change, Delete and Revert.
If I click New Partition Table I get this message "You have selected and entire device to partition. If you proceed with creating a new partition table on the device, then all current partitions will be removed."
If I select the partition /dev/sda4  ntfs (where I want to install Ubuntu) and click on New partition table, nothing happens.

---

### Post by Ymurti on 2012-10-24
Solved I managed to install Ubuntu. Here it is what I did. I have chosen Try Ubuntu, then I open Gparted and I deleted sda3 and sda4. Then I have chosen Install Ubuntu and there came the option "Install Ubuntu alongside Windows 7". I clicked on it and the installation is going on nicely. Thank You all for the help. I have learned more about Ubuntu.

Hare Krishna!

---

### Post by Bucky Ball on 2012-10-25
Excellent work. As I mentioned, you can't install Ubuntu on an NTFS or FAT partition. You need and EXT*, which it will create on free space during install, or you need free space to create EXT* partitions and install to.

Good luck, enjoy, and post a new thread with any further issues.

---

