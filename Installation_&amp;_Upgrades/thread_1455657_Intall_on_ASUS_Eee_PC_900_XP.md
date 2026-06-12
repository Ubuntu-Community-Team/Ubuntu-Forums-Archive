---
title: "Intall on ASUS Eee PC 900 XP"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by Jdinga on 2010-04-16
I have newly acquired an ASUS Eee PC 900.  It had XP loaded and I a trying to load Ubuntu Remix 9.10.  The primary SSD is 4G and the other is 8G.  I did notice that if you bought the Linux version of this PC, the primary SSD was 8G.
 The PC runs from the USB great and I am trying to get it installed permanently with no luck.  While Preparing Disk Space, I select the “erase and use the entire disk option”.  After about 15 minutes, a pop-up says “Do you want to resume partitioning” The attempt to mount a file system with type ext4 in SCSI2(0,0,0), partition #1(sda) at / failed.  You may resume partitioning from the partitioning menu.  There are two options, Go Back or Continue with both options taking me back to the menu.


  After reading this forum, I copied and attached the results of the attempt. 



Also, I tried loading easy peasy 1.5 from USB and it failed due to insufficient disk space.  Easy Peasy runs from USB also.  Any ideas of how I may proceed?  Thanks
 

 ubuntu@ubuntu:~$ sudo fdisk -l  
 

 Disk /dev/sda: 4034 MB, 4034838528 bytes  
 255 heads, 63 sectors/track, 490 cylinders  
 Units = cylinders of 16065 * 512 = 8225280 bytes  
 Disk identifier: 0x000100c1  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1               1         461     3702951   83  Linux  
 /dev/sda2             462         490      232942+   5  Extended  
 /dev/sda5             462         490      232911   82  Linux swap / Solaris  
 

 Disk /dev/sdb: 8069 MB, 8069677056 bytes  
 255 heads, 63 sectors/track, 981 cylinders  
 Units = cylinders of 16065 * 512 = 8225280 bytes  
 Disk identifier: 0x0003071f  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sdb1   *           1         606     4867663+  83  Linux  
 /dev/sdb2             607         981     3012187+   5  Extended  
 /dev/sdb5             933         981      393561   82  Linux swap / Solaris  
 /dev/sdb6             607         910     2441817   83  Linux  
 /dev/sdb7             911         932      176683+  82  Linux swap / Solaris  
 

 Partition table entries are not in disk order  
 

 Disk /dev/sdd: 2055 MB, 2055019008 bytes  
 16 heads, 63 sectors/track, 3981 cylinders  
 Units = cylinders of 1008 * 512 = 516096 bytes  
 Disk identifier: 0x00000000  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sdd1   *           1        3982     2006823    b  W95 FAT32

---

### Post by tom4everitt on 2010-04-16
What about choosing manual partitioning? Then you can manually choose to erase all partition, and create an ext4-partition (with mount-point '/') and a small swap partition.

Apart from that a manual installation is not more complicated than an automatic.

---

### Post by ajgreeny on 2010-04-16
All I can suggest is for you to try deleting all the partitions on sda manually with gparted, and then try either to install the OS onto a clean unallocated disk, or again using gparted make the partitions you want, then choose manual partitioning at that stage of the installation.

I have always used manual partitioning since my second install of ubuntu (v5.10) as I feel it gives much more control, and I also have a separate /home partition so need to keep that mounted as /home every time I install a new updated version.

EDIT:-
Too slow again, but at least it's more or less the same answer.

---

### Post by Jdinga on 2010-04-16
Thanks for the quick response.  I can try that but since this is new to me, I am not really sure which partitions I need and don't need.  Are the only two partitions needed at this point a ext4 with a mount point of / and a small swap?

---

### Post by ajgreeny on 2010-04-16
> **Jdinga said:**
> Thanks for the quick response.  I can try that but since this is new to me, I am not really sure which partitions I need and don't need.  Are the only two partitions needed at this point a ext4 with a mount point of / and a small swap?
Yes, that's really all you normally need, but see my comment below about swap.  On a bigger disk you might use a separate /home partition but there is not really room to play with that possibility on just 8GB.

You don't need another swap partition as there is already one of those on the original 4GB SSD, so you can simply make a single ext4 partition on the whole 8GB disk.

---

### Post by snowpine on 2010-04-16
I would recommend skipping swap entirely and just using one big ext4 partition for your / (root) partition.

Swap is not good for SSD's and it is only necessary if 1) your computer has very little ram; or 2) you intend to use the Hibernate feature (in which case swap must be larger than your ram).

---

### Post by Jdinga on 2010-04-16
Thanks all, I am up and running sans the USB.  I configured the 8G as ext4 / with a 567 swap area.  I configured the 4G as ext4 /home with a 526 swap area.  I now am convinced it works and wlll probably mess around wth the configuration once I learn more about it.  I will probably get rid of the swap area since it s not good with SSD's.  Thanks again.

---

### Post by Jdinga on 2010-04-17
I thought that I loaded the / on the 8G SSD but it turns out that the BIOS apparently cannot be configured to boot from the 8G.  I reloaded the machine multiple times after my last post because the system would eventually crash upon rebooting and would not start up.  It does not crash every time but it did crash at least one time in 5 boots.  it complains about corruption on the 8G drive.  If I knew what I was doing, I could probably get past the failure but since ubuntu is new to me I always end up reloading (very time consuming).  I  tried many combinations to use the 8G  but it seems like whenever I use it, the system fails eventually when restarted.  (I do execute a shutdown each time I try the restart)
The configuration I am now using that seems to be working is the / mount on an ext4 with no swap on the 4G and I am not using the 8G,  So far so good but I don't have much space.

---

### Post by tom4everitt on 2010-04-18
But when you've booted from the 4gb hard drive, aren't you able to mount the 8gb one from Places (in the top left menu)?

Another option would be to create an ext4 on the entire 8gb drive, and mount that as /home. Then you would have 4gb for your system, which is enough if you don't install anything big, and 8gb for all your userfiles.

---

### Post by Jdinga on 2010-04-18
I tried making the 8G an ext4 with /home while partitioning and the system will not come up after about 5 shutdowns complaining about errors on the sdb (8G).
I'm not sure where Places is.
I would be happy if I had to mount the drive each time I wanted to use it and unmount it after using it.  Using it for data files only.  Maybe then it would not be relying on the 8G to come up?.
Can you point me to somewhere that would explain that or can you share that info if it not too involved?

---

### Post by tom4everitt on 2010-04-18
With places I just meant Places to the top left of your desktop. On the top bar. To the left. Between Applications and System. You know where I mean?

In that menu, all detected hard drives etc. comes up. Clicking on one usually mounts it to /media.

---

### Post by callmeray on 2010-04-18
I've got a Linux 900 (Celeron) that has a 4 (sda) and a 12 (sdb). I'd recommend you put / on the sda and /home on the sdb. I've run several distros on it including Ubuntu NBR and eeebuntu, I generally recommend the latter for that particular box.

---

### Post by Jdinga on 2010-04-18
When I originally did the partitioning, I selected “Do Not Use” on the 8G.  Now that I want to use the 8G and manually mount and unmount it, I selected System > Disk Utility and created a partition of type   ext4 on the 8G drive.  Once that completed, I was able to see the 8G in Files and Folders but it would not open, but, if I double-click Documents and select the 8G in the left pane, I can click it, enter password and mount it.  This will be perfect and hopefully I will get past all the crashes.  If I run into problems, I will post another message.  Thanks for sticking with me.  
 I did try easypeasy because I read it was the eeeubuntu version but it failed the install due to not enough disk space when loading on the 4G only.  When I try and put the /home on the 8G the system would not restart more than 4 times.

---

### Post by callmeray on 2010-04-18
> **Jdinga said:**
> I did try easypeasy because I read it was the eeeubuntu version but it failed the install due to not enough disk space when loading on the 4G only.
easypeasy != eeebuntu.

---

### Post by Jdinga on 2010-04-18
My mistake, I saw this:
[http://forum.eeeuser.com/viewtopic.php?id=66407](http://forum.eeeuser.com/viewtopic.php?id=66407)

---

