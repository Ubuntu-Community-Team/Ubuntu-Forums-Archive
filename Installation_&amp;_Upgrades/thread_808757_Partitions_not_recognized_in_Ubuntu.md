---
title: "Partitions not recognized in Ubuntu"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by Alt-A on 2008-05-26
Dear Friend

I have been trying for 2 days now to install ubuntu I have read countless articles downloaded numerous programs(gparted which I could not get to work) to help at no avail, the problem I am having is the partioner will not recognize my partions in the ubuntu desktop install (download iso burn and use it to boot) the version i am installing is 8.04 LTS.  I get to the partition stage however nothing is recognized.  
I am trying to do a dual boot win xp pro and ubuntu.  I have a 500g hard drive I have partioned as follows 12gb for windows xp 19.53 gb for applications, 300gb for media and the rest as an unallocated space for ubuntu, all partions were done at time of winxp install then using disk management in windows to partition drives.
I am unable to determine how i can get ubuntu installer to see any of my partitions your help is greatly appreciated.  
By the way, I am totally brand new to Linux, Ubuntu.

---

### Post by Patb on 2008-05-26
Try starting Ubuntu from a live CD and then open a terminal.  Then post the output of:
```
sudo fdisk -l
```
This should give a list of partitions which might show how to address the problem.  

Cheers, Pat.

---

### Post by Alt-A on 2008-05-26
not really sure what to do with the command lines

---

### Post by Patb on 2008-05-27
> **Alt-A said:**
> not really sure what to do with the command lines
No worries mate! :). Take your time and people here will help.  

First boot the live CD if you can.  Just put it in the CD drive and start the computer.  At the prompt, choose the line something like "Try Ubuntu without changing your computer".  You might need to set your bios to start from the CD so if you don't know how to do that, you could ask someone or do a search.  

If you get it to start Ubuntu, open a terminal (Applications > Accessories > Terminal).  In that terminal, type "sudo fdisk -l".  That is a lower case L, not a 1.  Hit return and you should see a printout of the partition information.  Select that with your mouse and hit Ctrl-Shift-C to copy it.  Then paste the output into a response on this thread (Ctrl-V).  If you want, you can select it there and hit the button marked "#" at the top of the message box.  That will put it into a code box the likes of which you will have seen on this forum.  

Try it and see.  Cheers, Pat.

---

### Post by hts3813 on 2008-05-27
> **Alt-A said:**
> Dear Friend

I have been trying for 2 days now to install ubuntu I have read countless articles downloaded numerous programs(gparted which I could not get to work) to help at no avail, the problem I am having is the partioner will not recognize my partions in the ubuntu desktop install (download iso burn and use it to boot) the version i am installing is 8.04 LTS.  I get to the partition stage however nothing is recognized.  
I am trying to do a dual boot win xp pro and ubuntu.  I have a 500g hard drive I have partioned as follows 12gb for windows xp 19.53 gb for applications, 300gb for media and the rest as an unallocated space for ubuntu, all partions were done at time of winxp install then using disk management in windows to partition drives.
I am unable to determine how i can get ubuntu installer to see any of my partitions your help is greatly appreciated.  
By the way, I am totally brand new to Linux, Ubuntu.

I have a similar problem and I think the problem is in the number of partitions Ubuntu can recognise. Just like you, I am new to linux, so I tested on my old 40gb drive with only 2 partion. One holding XP pro and the other was empty. Ubuntu install fine and without any hitches. It was when I decided to install on my larger drive whith 4 partitions, the problem you are in showed up.

If there is any one out there with suggestions to fix, we will appreciate.

---

### Post by Patb on 2008-05-27
> **hts3813 said:**
> ...If there is any one out there with suggestions to fix, we will appreciate.
Hts, the only suggestion I can make is what I suggested in posts #2 and #4 in this thread.  That information should help more experienced users to see what partition setup you have and possibly assist.  If you can follow the instructions there, please post your partition listing.  If there is some impediment to doing that, please post the details and someone should be able to help.  

You can have only 4 primary partitions.  However one partition can be an extended partition and within that there can be numerous logical partitions.  

Cheers, Pat.

---

### Post by rbmorse on 2008-05-27
Alt-A: Something else you can try: When the installer gets to the partitioning screen, select "manual." The next screen should present a list of partitions on the drive and well as indicate unpartitioned space. Double click on the unpartitioned space entry to open a modification screen. Enter a "/" in the mount point dialog, select EXT3 from the format dialog and size as desired. 

Don't forget to leave 2Gb or so for a swap partition. You create that by double clicking on the unpartitioned space left after you set up "/" and select swap from the partition type pulldown.

---

### Post by Snort44 on 2008-05-27
> **rbmorse said:**
> Alt-A: Something else you can try: When the installer gets to the partitioning screen, select "manual." The next screen should present a list of partitions on the drive and well as indicate unpartitioned space. Double click on the unpartitioned space entry to open a modification screen. Enter a "/" in the mount point dialog, select EXT3 from the format dialog and size as desired. 

Don't forget to leave 2Gb or so for a swap partition. You create that by double clicking on the unpartitioned space left after you set up "/" and select swap from the partition type pulldown.

I'm having the same problem it seems.  Trying to install 8.04 16 bit to a 160 gig HD with 4 partitions.  In install, I click on "Manual" and it takes me to a screen that only shows the whole HD with no partitions.  But, when I run the live CD, the partitions are there and mountable. The CD is from Ubuntu, not downloaded and burned. Any help would be appreciated. I realize I haven't posted any partition info yet.  I'll try to retrieve it now.  -Snort44

---

### Post by Snort44 on 2008-05-27
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4985    40041981   83  Linux
/dev/sda2            9727        9848      979965   82  Linux swap / Solaris
/dev/sda3            4986       16876    95514457+   5  Extended
/dev/sda4           16877       19457    20731882+  83  Linux
/dev/sda5            4986        9726    38082051   83  Linux
/dev/sda6   *        9849       13687    30836736   83  Linux
/dev/sda7           13688       16876    25615611   83  Linux

Thanks, Snort44

---

### Post by Patb on 2008-05-27
> **Snort44 said:**
> ... In install, I click on "Manual" and it takes me to a screen that only shows the whole HD with no partitions.  But, when I run the live CD, the partitions are there and mountable.
Snort44, that is strange behaviour.  I cannot understand why your HDD is not being recognised during install.  It might be worth trying to install from the alternate CD.  

From your partition information, I do wonder why /dev/sda6 has the boot flag in addition to /dev/sda1, but I don't think it will do any harm.  You said the disk had 4 partitions, so I'm assuming you mean primary partitions, ie the extended partition, /dev/sda3, contains /dev/sda4,5,6 as logical partitions and that /dev/sda7 is another primary partition.  If it is any help, there is a page on how to partition at [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

I hope someone can help explain why your HDD is not being recognised during install.  

Cheers, Pat.

---

### Post by Alt-A on 2008-05-31
I have tried to install from an alternate cd and now i think I am getting closer to what the real problem is.  Ubuntu does not recognize my disk drive and it gives me a list of drivers to choose from but I have no idea what to choose. The hard drive I have is a western digital (
WDC WD5000AAKS-75YGA0 [Hard drive] (500.11 GB) -- drive 0).
Hope someone can help I really do want to try and use ubuntu.

---

### Post by black drongo on 2008-06-01
hi i have the same problem.i was using gutsy and for hardy i wanted a fresh install.i am using a live DVD. but hardy is not showing my partitions in the partitioner in manual mode (in Gparted HD shows as unpartitioned space) though they are visible in the computer and mountable.my partition info is

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cbd09

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/sda2            1021        1281     2096482+  82  Linux swap / Solaris
/dev/sda3            1282       20023   150545115    f  W95 Ext'd (LBA)
/dev/sda4            3632        6242    20972826    7  HPFS/NTFS
/dev/sda5            1282        2497     9767457   83  Linux
/dev/sda6            2498        3631     9108823+  83  Linux
/dev/sda7            6243        8853    20972826    7  HPFS/NTFS
/dev/sda8            8854       11464    20972826    7  HPFS/NTFS
/dev/sda9           11465       16107    37294866    7  HPFS/NTFS
/dev/sda10          16108       20023    31455238+   7  HPFS/NTFS
```

i haven't faced this problem in previous installations(gutsy,edgy..) any ideas?
thankyou in advance

---

### Post by black drongo on 2008-06-02
hi mine is solved. thanks to 
 pumalite and the software testdisk. i understand that the problem with partitioner was the presence of overlapping partitions.test disk pointed it and corrected it. i have installed hardy now.
try this links 
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by black drongo on 2008-06-02
hi mine is solved. thanks to 
 pumalite and the software testdisk. i understand that the problem with partitioner was the presence of overlapping partitions.test disk pointed it and corrected it. i have installed hardy now.
try this links 
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

