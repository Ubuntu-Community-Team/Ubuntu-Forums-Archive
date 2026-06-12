---
title: "Help with install - manual parition"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by pizzicar on 2007-03-31
Hello,

Running a windows XP system with 2 drives. I downloaded the live ISO and ran the CD. The CD booted fine and after playing, I decided to install.

I ran the install program and it when through the installation fine - When it was time to reboot, I received a grub error 17 and it would not boot past that point so I could not get into either windows or ubuntu.

I booted with the XP install disk and went into the recovery console and did a fixmbr - at this point the system would boot normally into XP. I put the iso CD back into the drive and I am now back at the live desktop. 

I decided to install again, and I am at the partitioning section of the install. Because the partitions are already there, I figure a manual partitioning would be best.

The prepare partitions screen looks like this:

/dev/sda
  /dev/dsa1   ntfs    /media/sda1    
/dev/sdb
  /dev/sdb1 ntfs     /media/sdb1
  /dev/sdb2 ext3    /media/sdb2
  /dev/sdb5 swap 

I'm a bit green here - it tells me that I need to allocate space for a root partition - not sure what to do there.

or

given that all the files are there - do I just need to run grub and make the right assignments (not sure what those would be).

I would really appreciate any help on this. Thanks.

---

### Post by johnc4510 on 2007-03-31
Change the /dev/sdb2 ext3 partion to / instead of /media. / is the root partition.

---

### Post by pizzicar on 2007-03-31
OK - thanks - that worked. The install completed fine but upon reboot - I again get a grub error 17 and the system won't boot again. The install root and swap are on drive D: so I assume that this has to do with the error. 

Not sure what to do at this point.

---

### Post by Herman on 2007-03-31
> Grub error 17 : Cannot mount selected partitionThis error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.                                     If you get this error when trying to boot Linux, take a look at your /boot/grub/menu.lst file and make sure to check your operating system entry's 'root (hdx,y)' details are correct.
                                    
                                    You can use a [Super Grub Disk]("http://supergrub.forjamari.linex.org/") to boot Ubuntu for you so that you can easily check and repair your operating system's entry in menu.lst. 
Your install is on your number 2 two hard disk, so after booting with Super Grub Disk, you should  to go to  the 'advanced' super grub menu and use that menu.  
Choose  'Gnu/Linux Advanced', then  'Boot Gnu/Linux Directly'. 
Choose 'same root and boot partiton', and then 'SCSI', then choose hard disk number 2, and finally, choose partition 2, and that will boot Ubuntu up by it's symlinks, thus bypassing your faulty grub menu for now.

Then you just have to edit the Grub menu. If you aren't sure how to do that then please post a copy of the bottom part of that here. You can access it with 'sudo gedit /boot/grub/menu.lst' ```
sudo gedit /boot/grub/menu.lst
                                    
```And also just to make sure, if you could post the output from 'sudo fdisk -lu' as well it might be handy, please.```
sudo fdisk -lu
```


Super Grub DIsk will also be able to boot Windows for you for the time being too. 
Regards, Herman :)

---

