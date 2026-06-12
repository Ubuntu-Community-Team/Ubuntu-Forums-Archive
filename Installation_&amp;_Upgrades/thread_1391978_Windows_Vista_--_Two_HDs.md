---
title: "Windows Vista -- Two HDs"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by virsto on 2010-01-27
I have Windows Vista installed on one of my physical HDs (my C:\ drive with a 250GB capacity). My other physical HD (with D:\ and E:\) has a 750GB capacity and over 500GB free. 
 
I am completely new to Ubuntu and have prepared a CD for installation of vers. 9.10-desktop-i386. I would like to place it on the same physical drive as D:\ and E:\. I have also just finshed a complete backup of this HD.
 
Should I partition the HD (containing D:\ and E:\) before starting the installation, and if yes, how should I perform this partitioning? 
 
Thank you!

---

### Post by darkod on 2010-01-27
If you finished a complete backup of the second hdd, and assuming windows installation is on C:, the easiest thing is deleting all partitions instead of resizing.
Boot with ubuntu cd, Try Ubuntu option, and open Gparted (System-Administration). Top right select the correct hdd.
Delete all partitions on it. Click the big green tick mark button in Gparted toolbar to execute your commands (otherwise they are just shceduled and exiting Gparted will not make any change on your hdd).
Then create one or two primary partitions as ntfs, with size as much as you want. Leave the rest of the hdd as unallocated, do not create any partitions for linux at that moment. Again you have to execute the commands with the green button.
When that is done reboot without the cd in windows and check if all is fine. Put back your data in the newly created partitions but keep your backup still.
Go into BIOS and make the second drive to be first boot option.
Then boot with the ubuntu cd, Install Ubuntu option, and in step 4 tell it to Use Largest Available free space (the unallocated space you left) and it will install ubuntu there. Or create partitions manually into that space if that's what you want and if you know how to do it. In the last screen, before clicking Install, click on Advanced and make sure the bootloader is installed on the second disk, probably called /dev/sdb. You can see what it was called in step 4.

That's it.
In case the ubuntu installer in step 4 shows you the first disk, briefly select the Erase and use whole disk option (just temporary). That will enable the drop down list under it and select the second disk there. Then make sure you select the Use Largest Available Free space option and proceed forward.

---

### Post by virsto on 2010-01-27
I would like to keep Windows Vista (at least for awhile) and my backups are disk image backups, thus it seems resizing should be used --- is this correct?
 
--V

---

### Post by darkod on 2010-01-27
> **virsto said:**
> I would like to keep Windows Vista (at least for awhile) and my backups are disk image backups, thus it seems resizing should be used --- is this correct?
 
--V

Not sure, it would depend on the backup software. Most software won't mind restoring to partition of different size as long as there is enough space to restore all of the data.

For example, if you image a 100GB system partition I see no reason not to be able to restore onto 80GB partition as long as the image is less than 80GB.

---

### Post by oldfred on 2010-01-27
If you have 500GB free in your 750GB drive you may only have to resize one partition, the last one on the drive. Shrinking and moving data can be very slow especially for large drives. Darko's way is the easiest, but Ubuntu does not need a lot of space if you are putting most of your data in the NTFS partitions anyway. 

Ubuntu can be installed in 10-20GB for root with swap equal to RAM if you ever want to hibernate or about 2GB otherwise if you have a lot of memory. You may want /home to be separate and it should be large enough for your data. I now have some data in a NTFS partition to share with windows (which I now after 3 years use very little) and a new /data partition just for most data. My /home is now only 1GB since it has no data just (hidden)system settings and links to the data.

If all you are making is 10-20GB for root, 2GB for swap and 20-40GB for /home, you may not have to move much data in the existing NTFS partition(s). I would defrag and clean up your NTFS partitions and try to shrink the last one and see if it takes a long time or not.

---

### Post by kansasnoob on 2010-01-28
I recommend beginning just by getting used to Ubuntu and Gparted, that is boot the Live CD choosing to try without changes (after checking disc for integrity) and have a look around.

Go to System > Administration > Gparted and have a look around. Don't make any changes just yet!

You'll notice in the upper right hand corner you can "toggle" from one drive to another, most likely sda and sdb. You'll notice partitions numbered like sda1, sdb1 sdb2, etc.

Quite simply the a in sda means drive #1, the 1 in sda1 means partition #1, etc. Chances are your data drive, where you want to install Ubuntu, will be sdb.

Take plenty of time to figure out exactly what's what. You may be more comfortable using Vista's partitioning tool to resize your existing partitions before continuing.

I'd then use Gparted to create the partitions for Ubuntu. Remember there's a 4 primary limit so I'd just create one extended partition and then create logical partitions for Ubuntu within it.

Look what I've done here:

[ATTACH]145214[/ATTACH]

Lots of logical partitions within the light blue extended partition :D

I prefer creating a root "/" partition and a "/home" and a SWAP because having a separate /home allows for re-installation without data loss.

The following tutorial shows generally what I do, creating partitions with Gparted, and then installing to the pre-created partitions using the Manual (Advanced) installation option:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Take your time to plan and ask more questions if needed.

---

### Post by virsto on 2010-01-31
I have been studying material on installing Ubuntu while keeping my Windows OS, and I still am puzzled by the installation process when one has more than one HD. That is, my situation does not seem to be covered --- I probably am missing something. 
 
Currently my primary HD, Disk0 (232.88 GB NBTFS) has partitions: System, Boot, Page File, Active, Crash Dump. My secondary HD, Disk 1 (698.64 GB NTFS) has two Primary partitions: MISC (D: of 349.25 GB NTFS, and APPLIC (E: of 349.39 GB NTFS. 
 
**Disk 0** is where Windows Vista and many Windows application programs reside and currently has 143 GB free space. I would like to keep this disk dedicated for Windows software.
 
**Disk 1** is where I would like to put Ubuntu BUT NOT THE ENTIRE HD.:KS
 
When I turn-on my PC I would like to be able to choose to either boot from Disk 0 (where I have my Boot partition for Windows) or to boot from Disk 1 where Ubuntu would be located.
 
How should I install Ubuntu so that I can put Ubuntu in it's own partition on Disk 1?

---

### Post by darkod on 2010-01-31
1. Boot vista and defrag D: or E: depending which you want to shrink to make space for ubuntu.
2. Use vista disk management to shrink the selected partition by as much as you plan (at least 25GB for ubuntu, the more the better).
3. Boot vista few times to make sure it's happy after the shrink.
4. Go into BIOS and make disk 1 before disk 0 in the hdd boot order.
5. Boot with the ubuntu cd and select Install Ubuntu. In step 4, tell the installer to use Largest Available Free space (you created with the shrink) on the 750GB disk. Also note how the disk is called, /dev/sda or /dev/sdb.
6. IMPORTANT: In the last screen, before clicking Install, click on Advanced and make sure the bootloader (grub2) will be installed on the same disk, /dev/sda or /dev/sdb depending how it's called.

That's it.

---

### Post by virsto on 2010-02-01
I have followed the suggestions that have been posted, studied a book on Ubuntu, and then started the installation process with my goal to install Ubuntu in a large partition (156 GB) created in Windows Vista. This I described in more detail in my previous postings. This is the largest free space on all my HDs. 
 
I then started the installation and everything went well until I came to the actual management of the partitioning. My plan was to follow the menu and install on the largest free partition (which was this 156 GB partition on D:\. However, at the top of the display there was a message saying "There is no operating system on this computer...". This bothers me greatly! Does it not recognize that Windows Vista is installed and has a boot partition that I need to keep intact on C:\?
 
How should I interpret this "...no operating system..." message and should I go ahead with "Use the largest free space"? 
 
My goal is to have both Windows Vista and Ubuntu on my PC.
 
--V

---

### Post by darkod on 2010-02-01
> **virsto said:**
> I have followed the suggestions that have been posted, studied a book on Ubuntu, and then started the installation process with my goal to install Ubuntu in a large partition (156 GB) created in Windows Vista. This I described in more detail in my previous postings. This is the largest free space on all my HDs. 
 
I then started the installation and everything went well until I came to the actual management of the partitioning. My plan was to follow the menu and install on the largest free partition (which was this 156 GB partition on D:\. However, at the top of the display there was a message saying "There is no operating system on this computer...". This bothers me greatly! Does it not recognize that Windows Vista is installed and has a boot partition that I need to keep intact on C:\?
 
How should I interpret this "...no operating system..." message and should I go ahead with "Use the largest free space"? 
 
My goal is to have both Windows Vista and Ubuntu on my PC.
 
--V

In some cases with more than one hdd, by default the suggested hdd will not be the one you plan to install onto. In this case you can try the following:
1. Select Erase and use whole disk option (even if you do not plan to use it)
2. This will enable a drop down list under it. Select the disk you want to install onto.
3. Then select the Use Largest Available Free space option. DO NOT FORGET THIS! DO NOT PROCEED WITH THE ERASE OPTION SELECTED!!!

In the lower part of the screen you should see a colored bar representing your hdd partitions how it will look like after the install. You can also pay attention to this bar to make sure you're getting the layout you wanted.

---

### Post by virsto on 2010-02-01
Eureka! :p
I have Ubuntu installed in the 156 GB partition, and Windows Vista is still intact. The installation went very well, with the exception of one small detail. I selected my time zone as instructed (Stockholm, Sweden) and the time was incorrect (it was one hour ahead). 
 
Thanks for the help given and esp. to "darkod".
 
Hopefully, I will be able to phase out Windows soon, and become an Ubuntu user.
 
--V

---

