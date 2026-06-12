---
title: "Worried about my installation!"
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by PadiSka on 2012-01-24
I made 3 logical partitions to install ubuntu and Im worried about the space I allocatated and if it was enough!

The 1st partition I made was for the swap area and I allocated 8Gb of space for this!


The 2nd partition I made was for the root of the OS. Using ext4 jourling file and mount point /. I allocated 10Gb of space for this.


The 3rd logical partition I made using ext4 jourling file and mount point /home. I gave this partition then the rest of available space (which at the start was 20Gb) The rest of the space was just under 3 Gb which seems very little and I was worried was this enough space for the 3rd partition!

So basically I wanna know did I give this 3rd partition enough room and what is it for and will a smaller space end up slowing something down!


Thanks for any help! I apreciate it!

---

### Post by darkod on 2012-01-24
Having a small /home partition will not slow anything down, the / (root) partition is the main one.

However, all your documents, music, videos, downloads, etc are stored in /home by default since your home folder is there. So having a small /home will affect how much you can save there.
Also program settings and configuration are there but usually this doesn't need much space in linux.

Why did you make your swap 8GB? That sounds much if you only had 20GB in total to allocate.

---

### Post by sudodus on 2012-01-24
Please describe what you have (computers specs), and how you want to run your computer! I agree that 8GB seems too much (40% of the available space) for swap. Otherwise 20 GB is OK for Ubuntu, but once you start collecting private files, you will fill the disk space, unless you get a bigger drive or use an external drive for big files (photos, videos etc).

With only 20 GB, I would make one partition for Ubuntu and a smaller swap partition. Are you planning to use hibernation? In that case you need at least the same size as the RAM, otherwise it can be smaller.

---

### Post by PadiSka on 2012-01-27
Thanks guys for the help!

I was advised that a good a good swap file size was to double the size of your RAM. I have a vaio vista intel core2duo 320 hdd 4gb RAM ATI 1gb graphics card.

Can i increase the /home directory without reinstalling?

Also should I have made a /boot directory?

---

### Post by darkod on 2012-01-27
No, you don't need a separate /boot partition.

The advice is 1.5x to 2x of RAM for the swap partition, but not when you have 4GB of RAM and only want to allocate 20GB of HDD for ubuntu. The swap will take too much.

In fact, if you are not planning to use the hibernate function, a swap of 2GB is enough. You need at least 1.5x RAM for swap only if planning to hibernate because the content of the memory needs to be saved in the swap partition.

If you boot with the cd in live mode and open Gparted you should be able to resize swap and /home. Just be careful, and only resize, don't reformat them.

---

### Post by paulgault on 2012-01-27
check out [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

i thing you definitely count as High RAM and low disk space in the examples given.

swap is nice but not essential. it's useful for memory management and will help if your machine is lacking RAM but you've got a huge amount of memory there. 

IMHO i think you might be wasting disc space giving over 8 gig to swap. unless your going to be doing some pretty intense stuff the 4 gig of physical memory should do fine. maybe give it 1 gig of swap to be extra safe?

--

if this were my machine i'd boot from live CD and use gparted to re-arrange to have / as the first half of the drive, have a much smaller swap partition in the middle of the disc (or none) and have /home as the other half. FYI you can just delete the swap and make a new one when the others have been moved. there is no need to keep any of the data on the swap partition

--

there are benefits to having a separate /boot partition but it's not really necessary for a desktop and is more the kind of thing to worry about if you're setting up a server.

---

### Post by sudodus on 2012-01-27
> **PadiSka said:**
> Thanks guys for the help!

I was advised that a good a good swap file size was to double the size of your RAM. I have a vaio vista intel core2duo 320 hdd 4gb RAM ATI 1gb graphics card.

Can i increase the /home directory without reinstalling?

Also should I have made a /boot directory?
If you have plenty of space, double the size of your RAM is a good idea. But not now. Do you intend to hibernate the computer? In that case you need at least the size of RAM (4GB) for swap. Otherwise you can select any size, even zero, unless you know, that you will do some things, that demand a lot of memory. For example, if you like to have several applications running at the same time, and you have big documents, videos etc opened, you might run out of RAM. Then swap is saving the situation, but it will be very slow.

I think you can edit your partitions. First ***backup*** your system or at least your personal files. Start Ubuntu from your install CD or USB drive. Use ***Gparted*** from there, and move the boundary between adjacent partitions: first shrink one, then increase the other one. But it tends to be very time-consuming, so if you recently installed the system. It would probably be faster to reinstall the system. That means fast editing of partitions (without saving the data).

So it depends how much time you have spent to develop or tweak your system, if you should move the boundary between adjacent partitions keeping the data, or if you should reinstall the system.

---

### Post by nipunshakya on 2012-01-27
@PadisKa:
I think you have a dual-boot as you mentioned in your other thread. So i would pretty much like to see your partition scheme for your windows too...run gparted and post the screen result here. That would let me advise you some more on your current partition scheme.

Im asking you for this because, /home is more or less similar to your My Documents folder in windows. That partition can be used to store your backups too..... 
However, if you have an extra NTFS partition on your windows side, (maybe like c: for windows, d: for data etc)there is nothing to worry about your /home getting less coz u can use that space for your extra data storage thing. 
But u did too much in your swap-space. 8gib is double than what you need. Your hardware specs already give you enough ram to hibernate your system. So cut the share of swap down and you can allocate them to /home if you want(i'd go with darkod with this).

Lets see your partition scheme first.(run gparted and post a screenshot of it)

Regards,WinuxUser

---

### Post by PadiSka on 2012-01-30
@WinuxUser

Thank You for all your help and sorry for all the questions!ha.

Here are my screenshots! Also when I used the EASUS Partition Manager to view my partiton from windows I noticed that the "EASUS Partition Manager" and "EasyBCD" shortcut icons were bout missing their pictures, I dont suppose this is due to Ubuntu? Cos it never happened before.

So the swap area is just basically the same thing as pagefiles on windows? Virtual Memory?

---

### Post by sudodus on 2012-01-31
> **PadiSka said:**
> @WinuxUser

Thank You for all your help and sorry for all the questions!ha.

Here are my screenshots! Also when I used the EASUS Partition Manager to view my partiton from windows I noticed that the "EASUS Partition Manager" and "EasyBCD" shortcut icons were bout missing their pictures, I dont suppose this is due to Ubuntu? Cos it never happened before.

So the swap area is just basically the same thing as pagefiles on windows? Virtual Memory?
I think that Windows itself cannot (or does not want to) look inside linux partitions. But looking at the gparted picture it is evident that there is a lack of balance. There is a lot of free space in the Windows partition, and part of it might be used for linux.

This means editing partitions, which is risky. So you really need to backup your data. The best would be to make a cloned copy or an image of the whole hard disk drive to another hard disk drive (an external drive). I would use Clonezilla to do that. A minimum would be to backup all your personal data: documents, pictures, ...

---

### Post by nipunshakya on 2012-01-31
@PadiSka:

First thing, you dont need 8 gib for swap area. Boot to liveCd, right-click on that swap area and select "Swap-off", then resize it to just 4 gib. With that, you can get additional 4 gib , add it to home.(obviously, unmount it first to edit the partition)

Next, **you can extend a partition only if it has unallocated spaces to its right. **So , even if you wish to run disk management and shrink /dev/sda2 and take out some space out of it, you will have to move it to right of your current extended(/dev/sda3) linux-partition and its risky to do that...  so, first i must ask you,  **do u want to continue?** If you wish to continue, read carefully below and continue:
[https://help.ubuntu.com/community/HowtoPartition/MovingPartition](https://help.ubuntu.com/community/HowtoPartition/MovingPartition)
or you can start reading it from beginning to know more:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Hope they help you...Goodluck.

Regards,WinuxUser

---

### Post by nipunshakya on 2012-01-31
use gparted to make adjustments accordingly:
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
In my case, i too have a dual-boot machine in 320 gib hdd my friend. My partitions are as follows:
1. 60 gib for windows (primary partition c: as NTFS)
2. 60 gib NTFS (primary partition b:)
3. 142 gib NTFS (also primary partition e:)
4. an extended partition of ~36 gib for linux.
4.a. ~24 gib for / as ext4
4.b. ~10 gib for /home as ext4
4.c. ~3gib for swap area.

I use 2. and 3. as file sharing partitions between windows and Linux.
Since i use 2. and 3., i don't need much of a /home, but just in case i need a fresh installation, i will need it to import my current settings and all, so kept it just to ~10 gib. I guess that much would also be enough for you so don't worry as you have enough room on your NTFS filesystem.

Personally, i'd advise you to just decrease the swap area to ~3 gib and use rest to allocate for /home. That much must be enough for you. Don't mess with other partitions.Still, choice is yours

Regards,WinuxUser

---

