---
title: "please help to resize my SWAP partition without reinstalling UBUNTU"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by tech-hero on 2010-11-29
Hey, I'm starting to love ubuntu. i've tried different ways to install it and i finally get it done the way i love it. i've got limited internet connection so i really had a hard time downloading softwares, updates and some third party driver for my device.

i'm doing good until i've downloaded gparted.

i've found out that i only allocated 3 megabytes for my swap partition. i was plannning to give three Giga bytes but my mistake, i made it to 3megabytes.

i wanted to change it to 3gigabytes. my bad. i should have checked it carefully.

this is my dilemma. i love everything in my ubuntu now. the softwares and updates.i just want to fix this swap size.how can i do it without ruining everything in my ubuntu? if only there is a way to do this without reinstalling and reformating my ubuntu partition :(

should i use the live cd and use gparted and try to resize my swap memory? how??? 

here is my info for my system.

ive got 500GB of memory in hard drive

primary partition 50GB for windows system
primary partition 250GB for NTFS drive
primary partition 100GB for FAT32 drive

and

primary partition of 70GB for ubuntu in which 50GB is logical for /, 20GB for /home and 3MB for swap.

i need to change my memory for swap for at least 3GB..

i need your help guys. thanks.

---

### Post by mikewhatever on 2010-11-29
Yes, you can resize swap with Gparted on the live cd/usb. Make some unallocated space by shrinking a partition next to swap, then expand swap into the unallocated space.
After that, edit your Ubuntu fstab to use the new swap partition.

---

### Post by tech-hero on 2010-11-29
> **mikewhatever said:**
> Yes, you can resize swap with Gparted on the live cd/usb. Make some unallocated space by shrinking a partition next to swap, then expand swap into the unallocated space.
After that, edit your Ubuntu fstab to use the new swap partition.

thanks for the reply. im not so sure on the next partition to swap. can i use my /home partition for it? 

and also, what do you mean by fstab? how will i do it? thanks.

---

### Post by ajgreeny on 2010-11-29
You probably will not need to edit your fstab file as I don't think that enlarging it will change the UUID that identifies it.  If you made a *new* partition it would need a new entry for swap.

However, run the live CD and open up gparted.  Look for the swap partition in the listed partitions and right click on it to unmount it, as the live CD will probably be using it.

If the swap partition is numbered 5 or above, eg sda5, it is a logical partition enclosed in an extended partition, and you may need to enlarge the extended partition first.  It will be easiest to tell you exactly what to do if you can attach a screenshot of gparted, so we can see the layout of your partitions at the moment.

Don't worry about it being complicated to do; it is actually very easy once you get started.

Finally, yes, it is OK to shrink your /home partition, providing it has plenty of space.  Linux partitions tend to be much more forgiving than windows partitions if they are shrunk or enlarged or even moved.

---

### Post by tech-hero on 2010-11-29
> **ajgreeny said:**
> You probably will not need to edit your fstab file as I don't think that enlarging it will change the UUID that identifies it.  If you made a *new* partition it would need a new entry for swap.

However, run the live CD and open up gparted.  Look for the swap partition in the listed partitions and right click on it to unmount it, as the live CD will probably be using it.

If the swap partition is numbered 5 or above, eg sda5, it is a logical partition enclosed in an extended partition, and you may need to enlarge the extended partition first.  It will be easiest to tell you exactly what to do if you can attach a screenshot of gparted, so we can see the layout of your partitions at the moment.

Don't worry about it being complicated to do; it is actually very easy once you get started.

Finally, yes, it is OK to shrink your /home partition, providing it has plenty of space.  Linux partitions tend to be much more forgiving than windows partitions if they are shrunk or enlarged or even moved.

thank you very much for the instruction. i really don't want to mess up with my ubuntu right now. i love it. hope i could do it right at one try.

here is the screenshot of the partition of my partition via GParted:

[IMG]http://i238.photobucket.com/albums/ff136/nsm_x41/Screenshot.png[/IMG]

any help would be appreciated. thank you very much. im new to ubuntu, and im a little bit unfamiliar with technical terms.

---

### Post by ajgreeny on 2010-11-29
**BACKUP BACKUP-** Before you do anything to your partitions, make sure you have all your home folder/partition backed up properly.  Nothing *should* go wrong, but if it does, at least you have all your personal files available to restore.

You already have all your Ubuntu partitions as logical partitions in an extended partition, so that makes life a little simpler.  You also have a very large / (root) partition of 47.69GB of which only 3.8 is used, so I would shrink that to about 10GB, much more the normal size for root, by grabbing the left hand end and dragging it to the 10GB size I suggest.

To keep things simple, having seen you current setup, I would now delete the current swap, sda6, and make a new one, so right click on the swap and delete it.  Now make a new swap partition of 3GB in the unallocated space next to your root partition

Finally grab the left hand end of your /home partition sda7, and drag it to meet the right hand end of the new swap.  This move will take a long time, but should go smoothly; I've done it in the past with no problems, but make sure if using a laptop that you use mains power, not battery; you don't want the laptop to stop working or you will definitely be stuffed.

Once the /home has been enlarged, you should have root as 10GB, swap as 3GB and /home as the remainder of the space.

Still in the live CD run ```
sudo blkid
``` which will show the UUID of the new /swap partition.  You can now either edit the /etc/fstab of the installed ubuntu (not the live CD) by using ```
gksudo gedit /path/to/etc/fstab
```and removing the old UUID and replacing with the new one, or if you find that too difficult to sort out in the live CD, reboot.  The system should boot with no problem, though it may show an error about swap, but you can ignore that and then edit the fstab from within the install with ```
gksudo gedit /etc/fstab
```again just needing the new UUID in place of the old.

Your root and home partitions should still have the same UUIDs as you did not format them, merely shrink and enlarge.

Good luck!  If any problems appear, come back again.

---

### Post by tech-hero on 2010-11-29
> **ajgreeny said:**
> **BACKUP BACKUP-** Before you do anything to your partitions, make sure you have all your home folder/partition backed up properly.  Nothing *should* go wrong, but if it does, at least you have all your personal files available to restore.

You already have all your Ubuntu partitions as logical partitions in an extended partition, so that makes life a little simpler.  You also have a very large / (root) partition of 47.69GB of which only 3.8 is used, so I would shrink that to about 10GB, much more the normal size for root, by grabbing the left hand end and dragging it to the 10GB size I suggest.

To keep things simple, having seen you current setup, I would now delete the current swap, sda6, and make a new one, so right click on the swap and delete it.  Now make a new swap partition of 3GB in the unallocated space next to your root partition

Finally grab the left hand end of your /home partition sda7, and drag it to meet the right hand end of the new swap.  This move will take a long time, but should go smoothly; I've done it in the past with no problems, but make sure if using a laptop that you use mains power, not battery; you don't want the laptop to stop working or you will definitely be stuffed.

Once the /home has been enlarged, you should have root as 10GB, swap as 3GB and /home as the remainder of the space.

Still in the live CD run ```
sudo blkid
``` which will show the UUID of the new /swap partition.  You can now either edit the /etc/fstab of the installed ubuntu (not the live CD) by using ```
gksudo gedit /path/to/etc/fstab
```and removing the old UUID and replacing with the new one, or if you find that too difficult to sort out in the live CD, reboot.  The system should boot with no problem, though it may show an error about swap, but you can ignore that and then edit the fstab from within the install with ```
gksudo gedit /etc/fstab
```again just needing the new UUID in place of the old.

Your root and home partitions should still have the same UUIDs as you did not format them, merely shrink and enlarge.

Good luck!  If any problems appear, come back again.

wow. thanks for a very detailed explanation.

before i do anything else, i just want to clarify some things.

why do i need to shrink my root directory to 10GB? i haven't installed anything yet there. so im reserving alot for it.

next is, does changing or resizing the partition won't format the entire partition? i tried doing that with windows before, but it tells me that the partition would be formatted.

about the home folder, do i really need to allocate big space for it? why? where do the programs downloaded in ubuntu will be saved and installed? is it in /home or in the root? what if i use wine and install heavy programs? where should it be saved? in the root or home directory?

thanks in advance. cheers :)

---

### Post by mikewhatever on 2010-11-29
> **tech-hero said:**
> ...

about the home folder, do i really need to allocate big space for it? why? where do the programs downloaded in ubuntu will be saved and installed? is it in /home or in the root? what if i use wine and install heavy programs? where should it be saved? in the root or home directory?


Programs are downloaded and installed into the root partition, home is for personal files and program settings. Having a large home partition makes more space for personal files - videos, photos, documents, etc.

---

### Post by tech-hero on 2010-11-29
> **mikewhatever said:**
> Programs are downloaded and installed into the root partition, home is for personal files and program settings. Having a large home partition makes more space for personal files - videos, photos, documents, etc.

should i keep the root partition at 50GB? i rarely have personal and media files. if ever i have one, i kept them on the 100GB FAT32 partition. need more advice. :) thank you sir for the answer. 

This ubuntu community really rocks!

---

### Post by Quackers on 2010-11-29
I have 3 Ubuntu installations and none of the /root partitions is bigger than 13GB.
And none of those three is more than half full.
I was under the impression that user-installed programs went into /home, rather than the root partition.

---

### Post by tech-hero on 2010-11-29
uh oh. and now im being confused....

could someone explain this? i would really appreciate it and pay it forward to other people everything i'll learn.

---

### Post by mikewhatever on 2010-11-29
> **tech-hero said:**
> should i keep the root partition at 50GB? i rarely have personal and media files. if ever i have one, i kept them on the 100GB FAT32 partition. need more advice. :) thank you sir for the answer. 

This ubuntu community really rocks!

Yes, if you want to. It's not necessary to resize it.
Fat32 file system has limitations - lack of journaling, 4GB file size limit and fragmentation, other then that it's totally ok, especially if it suits your needs.

---

### Post by dino99 on 2010-11-29
standard installation:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by ajgreeny on 2010-11-29
As many have said, the root partition is the operating system, and if you have a separate /home partition, why bother having 50GB for root; I can not believe that even the most avid installer of applications would ever get near 50GB space filled.  My root partition has 4.5GB used out of 10, and I add lots of additional programs and applications other than the default ones in the installed version.  In the past I also had a full compliment of xubuntu-desktop and kubuntu-desktop as well as ubuntu-desktop, and even with those and all my other added programs still never got anywhere towards filling 10GB of root.

> Should i keep the root partition at 50GB? i rarely have personal and  media files. if ever i have one, i kept them on the 100GB FAT32  partition. need more advice. :smile: thank you sir for the answer. So what do you use your system for if you rarely have personal files?  We are speaking of all your documents, photos, music, videos, etc etc, and I can not believe that you do not have some of those.  You say they all go into the fat32 partition in order to be available to windows and ubuntu, and that is great, but if so I might ask why you bother with a separate /home partition.  Some config files and folders are there, I accept, but I still think this is a poor use of disk space, and would encourage you to have a smaller root partition, and if you want a separate /home to make that larger.  Alternatively forget about a separate /home and keep all your data etc etc in a partition formatted to fat32 or better, ntfs, which can be given read/write permissions from ubuntu in the /etc/fstab file.

Incidentally any programs you install in wine will be installed to your /home partition or folder, in a hidden folder called /home/username/.wine.  None of the wine programs go to root, except for the wine program itself, and that is not very big.  Other programs you install manually as opposed to using apt-get can be installed in various places, but are sometimes in /opt; it really depends upon how you install them and what the installing executable tells the system to do.

I hope that does not confuse you even further, but to my mind dino99's post says it all, more or less as I was suggesting.

---

### Post by tech-hero on 2010-11-29
> **ajgreeny said:**
> As many have said, the root partition is the operating system, and if you have a separate /home partition, why bother having 50GB for root; I can not believe that even the most avid installer of applications would ever get near 50GB space filled. My root partition has 4.5GB used out of 10, and I add lots of additional programs and applications other than the default ones in the installed version. In the past I also had a full compliment of xubuntu-desktop and kubuntu-desktop as well as ubuntu-desktop, and even with those and all my other added programs still never got anywhere towards filling 10GB of root.
 
So what do you use your system for if you rarely have personal files? We are speaking of all your documents, photos, music, videos, etc etc, and I can not believe that you do not have some of those. You say they all go into the fat32 partition in order to be available to windows and ubuntu, and that is great, but if so I might ask why you bother with a separate /home partition. Some config files and folders are there, I accept, but I still think this is a poor use of disk space, and would encourage you to have a smaller root partition, and if you want a separate /home to make that larger. Alternatively forget about a separate /home and keep all your data etc etc in a partition formatted to fat32 or better, ntfs, which can be given read/write permissions from ubuntu in the /etc/fstab file.
 
Incidentally any programs you install in wine will be installed to your /home partition or folder, in a hidden folder called /home/username/.wine. None of the wine programs go to root, except for the wine program itself, and that is not very big. Other programs you install manually as opposed to using apt-get can be installed in various places, but are sometimes in /opt; it really depends upon how you install them and what the installing executable tells the system to do.
 
I hope that does not confuse you even further, but to my mind dino99's post says it all, more or less as I was suggesting.
 
 
the truth is, i'm totally clueless with linux file system. im just starting to get myself used to it. somehow, i also have this obsessive compulsive syndrome. my windows got 50GB, that gave me a reason that UBUNTU should also have 50GB. i came from an 80GB desktop, but never even managed to fill 40GB with multimedia and programs. now, i don't know how to manage my 500GB HD. my bad oops.
 
i made a /home directory just to follow the typical UBUNTU installation. i don't know why. but i just feel like it being there. maybe if i want some documents not accessible to windows, i'll hide it there. im just starting to explore the possibilities and capabilities of UBUNTU. i'll change my settings after getting used to it. 
 
i'll try to change everything later at home. will update you guys about my progress. thanks for everything. i appreciate it so much. i really feel just like being a part of UBUNTU. it's a community :)

---

### Post by SeePU on 2010-11-29
tech-hero, it's always better to have 'extra' space rather than risk running out for any reason.  Imho, it's best to have TWO external drives as large as you can afford.   One, you install NTFS and put Windows data there.   The other one, you install the file format EXT3 or EXT4 and place anything you download or obtain for Linux.   This way, if you bork your main OS drive, your data is safe and it remains.

As for which partition to shrink to use towards your swap partition, I agree with the others who say to use it from your root partition.  It's not going to miss 3 or 4GB.  But, I think it's good to have it at least 20 or 30GB for sure.  One never knows.  Since, you already have it as 47GB or so, I think you can afford to have it 4GB smaller.  I'd leave the Home directory alone as it's good at 20GB.  My two cents.

---

### Post by tech-hero on 2010-11-30
> **SeePU said:**
> tech-hero, it's always better to have 'extra' space rather than risk running out for any reason. Imho, it's best to have TWO external drives as large as you can afford. One, you install NTFS and put Windows data there. The other one, you install the file format EXT3 or EXT4 and place anything you download or obtain for Linux. This way, if you bork your main OS drive, your data is safe and it remains.
 
As for which partition to shrink to use towards your swap partition, I agree with the others who say to use it from your root partition. It's not going to miss 3 or 4GB. But, I think it's good to have it at least 20 or 30GB for sure. One never knows. Since, you already have it as 47GB or so, I think you can afford to have it 4GB smaller. I'd leave the Home directory alone as it's good at 20GB. My two cents.
 
 
wow. thanks for the suggestion sir. i'll see what i can do later. i think, im just afraid to destroy everything in my root now because of resizing the partition. i don't want to end up installing ubuntu all over again. my ISP sucks. 
 
while /home folder for me is easy to manipulate because files there can easily be backed up. 
 
in case i want to extend my /home folder, could i get some from may fat32 partition?
 
thanks for the two cents. :)

---

### Post by tech-hero on 2010-11-30
Hi guys. I've followed your procedures with some variations. the hard part comes during the replacement of UUID. the sda numbers were changed since I deleted the old swap but i managed to solve it in gsedir fstab.

i restarted my pc , then look at sysinfo and checked the swap status.before I edit it says no swap but now, i have 2.63 GB swap.

thanks everyone for your help and support :) thanks for the efforts. ubuntu community rocks :)

---

### Post by SeePU on 2010-12-05
> **tech-hero said:**
> Hi guys. I've followed your procedures with some variations. the hard part comes during the replacement of UUID. the sda numbers were changed since I deleted the old swap but i managed to solve it in gsedir fstab.

i restarted my pc , then look at sysinfo and checked the swap status.before I edit it says no swap but now, i have 2.63 GB swap.

thanks everyone for your help and support :) thanks for the efforts. ubuntu community rocks :)Yeah, when you delete a partition, your 'partition naming' gets changed as you would notice your swap partition gets designated 'sdaN' (N being some number) and when you deleted it, the numbers shifted accordingly.  Some fstab editing can solve it.

I always try to plan out my partitioning scheme before my initial install.  What file formats I want, how large, where....etc.  It just makes it so much easier later on even though there's always a chance you'll want some change.  But, it makes it less likely you'll need something changed or easier if you do.  

Like I said before, I prefer 'data' on another drive whether it's ext3/4 or NTFS.    That way, when you do want to adjust partition sizes or formats, there's no worry of wiping out stuff and at worst, it's just a re-install of the OS.  One learns the hard way if you tend to download or copy your data on your OS drive.  If you have a backup, then it's no problem, too, though.

---

