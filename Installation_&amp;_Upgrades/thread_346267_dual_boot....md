---
title: "dual boot..."
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by biggsy137 on 2007-01-25
Hi. i want to install ubuntu on my pc so i can duel boot it with XP. this is the first time i have tried such a thing and wanted to check one thing before i make the leap of faith...

when you select the drive to install on (in my case the slave drive) and then select use most continuous free space, will it delete or alter any of the existing partitions? or will it just make new ones in the free space?

i have all my docs and music on the drive but have made space for ubuntu. i have also backed up what i can of the drive.

cheers!

---

### Post by kebes on 2007-01-25
When you get to the part of the installation where it is asking you where to install, I would suggest that you select 'manually'. You will be brought into a partitioning tool and you'll be able to select what partitions to create and how to allocate them. As long as you don't tell it to wipe your Windows partition, you won't lose that data.

The manual partitioner will also give you a confirmation before applying the changes. Make sure it doesn't list erasing/formatting the Windows drive and you should be fine.

(Of course, when making major changes to partitions a backup is always advised!)


Good luck!

---

### Post by biggsy137 on 2007-01-25
I did try the manual partitioner to begin with and got as far as the alocation step but that got a bit too confusing... any advice for using it?

---

### Post by kebes on 2007-01-25
Well, if the installer gives you a "use all free space" option then that's probably a safe bet. It should not touch your other partitions.


If you want to use the manual partitioner (gparted), you should get a graphical layout of your hard disk. You should see a listing for your Windows partition (probably NTFS), and a listing for "free space." You'll have to click in the free space and create an extended partition. Then click in that again and create at least a "root" and a "swap" partition. I think you can right click to add to the partition. Your swap should be about the same size as your RAM. The root partition can take up all the rest of the space.

You'll be given another screen where you have to associate partitions with mount points. The big partition is "root" and designated as "/" in most places. This is where all the linux files go. And then associate "swap" with the smaller one you made!

(You can also use create many partitions so that your user files in "/home/" are separate from the Linux operating system, which will be in "/". This is very useful but it's a complication you can ignore for now.)

---

### Post by biggsy137 on 2007-01-25
Thanks for the help! 

im just finishing backing up files etc so will be installing soon! :D Fingers crossed all goes to plan!

---

### Post by housam on 2007-01-25
Here is an example:
- 10 - 15G ext3 ( / ) for root
- 1G swap ( useless if more than 1G , you may not use it ever if you have 1G RAM or more.)
- 10-15 Gb is ext3 for /home

---

### Post by biggsy137 on 2007-01-25
well there, that was pretty painless!! :D

I'm replying now from my newly installed ubuntu OS! all seems fine so far...just downloading the updates before checking XP is still intact.

I used the 'use most free space' option in the end, seemed the easiest to begin with.

Thanks for all the help!

---

### Post by housam on 2007-01-25
Congratulations and welcom to ubuntu.

---

### Post by kebes on 2007-01-25
Cool! I'm glad it all worked out.

Note: ubuntu may already have mounted your XP partition. You can go "Places > Computer > Filesystem > Media" and you may see a foldered called "Windows" or maybe just "hda1" or something like that. Inside you should see your entire windows XP partition. (If you don't see this folder, don't worry... it can be easily added.)



Feel free to post if you have any more questions.

---

### Post by biggsy137 on 2007-01-26
It doesnt seem to be there... Windows seems to work fine too tho.

My disks are arranged something like this:

HDD0: PT0: Windows 
             PT1: Programs

HDD1: PT0: Data (my docs music etc)
             PT1: Ubuntu (how every it arranged its self)

In windows i cant see the Ubuntu partitions and in Ubuntu i cant see the windows partitions, i take it this is normal?

is it possible to make a patition thats FAT32 to swap files between the two OS, it would only be  open office docs type things?

---

### Post by kebes on 2007-01-26
Everything sound normal, yeah. You now have lots of options for sharing files:


1. Create a fat32 partition somewhere on the drive. Both Windows and Linux can read/write to this without trouble.

2. Install the "ext2/3" filesystem driver in Windows. This lets Windows read/write to Linux partitions. There are a few different open-source drivers written to do this ([here's one example]("http://www.ubuntuforums.org/showthread.php?t=268985")). I've never used them so I don't know how stable they are, or which is the best one. But I've been told that they run quite well.

3. In Linux, you can mount NTFS partitions. Linux has no trouble reading from NTFS partitions, so you can grab files from Windows easily. However the writing support is still considered "experimental." Some people have said it works perfectly, but some have also said that it eventually led to corrupted files.


Since you've already set-up your machine, the easiest is to use option #2. Keep all your user files on the Linux partition, and give Windows the ability to see those files. You can also activate #3 (in read-mode) in case you need a file from the Windows partition but don't want to reboot. It's up to you really.

---

