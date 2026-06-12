---
title: "Ignorant fool searching a partition genius"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by Samppa0 on 2006-06-15
Hello there..

I've been looking over the forums for the past few days but haven't found a solution so far, and I was hoping someone could either give me a hand or point me to the right direction>

My problem is this: I try to install ubuntu on to my hard drive, but when it asks me would I like to resize the master partition, erase, manual etc., I choose resize automatically, pick my size and before it begins it says not enough space to create partition. I have tried different sizes, and braved into the manual partioning area, but when I tried to resize the master partition and create another partition there, it says the same thing.

I've tried the live cd and the alternative install cd, no luck. I have defragged my harddrive multiple times (windows one), but it does still seem rather fragmented. I've identified this as my problem since free space is all over instead of being clearly defined, but that's only because I can't think of anything else (other than maybe having to partition before trying to install?). My harddrive is a whopping 40gb and I have about 18gb (it took a lot of cd burning) of free space according to "My Computer", the partition I've tried to create has ranged from 4gb to 10gb.

If anyone has any ideas they are more than welcome to share it, as I'd like to move into linux but it appears it's still proving as difficult to install as it was once :) 
Or alternatively, point me to a proper defragger.

Either way, thanks in advance!

---

### Post by yager on 2006-06-15
[QUOTE=Samppa0]I have defragged my harddrive multiple times (windows one), but it does still seem rather fragmented. I've identified this as my problem since free space is all over instead of being clearly defined, but that's only because I can't think of anything else[/QUOTE]

There is a much more efficient tool for defragmenting your XP drive.  I have used it and it works great, and....... ITS FREE.

[http://www.dirms.com/](http://www.dirms.com/)

The program is DIRMS and it will move every file to the front of your drive and put all of the free space at the end of the drive.  It is very efficient and will squeeze out every bit of free space from between the files.

To use it you will need an activation code which will work for 30 days.  You can renew every 30 days if needed or buy a license and not have to renew every month.  That is the only limitation to the program so it will work perfectly for you to get this one task done unless you take more than 30 days.  If you take that long to install Ubuntu, you are one dedicated fan.

---

### Post by Samppa0 on 2006-06-21
Well, thanks for the link, but it appears even that is not powerful enough.. I'm beginning to think my hard-drive is fookzored enough as to not being able to defrag properly. The defrag is stuck at about 4k or so fragged files and spaces and biggest continous free space of about 700mb, no matter how many defrags and reboots later. Not exactly full use of the available space..

I'm hoping there's another explanation apart from 'get ready for a format, big boy', and I was further hoping someone might have a clue on that as well :) 

Or alternatively, offer an even more efficient defragger that will force my hdd to sort itself out. I doubt it though..


A bit closer to an installation though:mrgreen:

---

### Post by bodhi.zazen on 2006-06-22
You have several options.

1. I advise you buy a new hard drive and leave you Windows drive alone. This is the easiest and least risky.

2. You can try GParted, but it (Gparted) has not been reliable for me. The biggest problem has always been in the way GPatred numbers partions. cfdisk is the most reliable method, but cfdisk will not re-size a partiton.

3. Several software tools will do this, all cost $$, none are guarenteed not to toast your windows partiton. Try partition magic or a Google search.

4. Xandros has performed the task at hand for me once in the past. Download the free version and try it. Install Xandros to HD and it will re-size windows for you. You can either keep xandros or install Ubuntu onto the xandros partition.

5. If you are willing to start from scratch, wipe the hadr drive, and install both Linux and Windows:

  First boot almost any Live Linux CD.
  Open a terminal and use cfdisk to re-partition your HD (this will toast any OS on the HD)

  I advise a 20 GB partion for Windows, a 15 GB partition for Linux, and a 5 GB FAT partition for data (to exchange data from windows to Linux easily). There are of course many variations on partioning including /boot partitions and a /home partiton.

 Next install Windows

 Last install Ubuntu and install GRUB to the MRB

---

### Post by Samppa0 on 2006-06-23
Yup, I've been thinking about a new hdd which would also solve my space problem..

Apparently it's the only way to go right now, thanks to both of you.

---

### Post by bodhi.zazen on 2006-06-24
Samppa0:

FYI: I was looking at Knoppix for another issue and came across documentation that claims the most recent version of Knoppix WILL RESIZE your windows partition for you (via GPARTED).

With Knopppix, the report claimed, all you need to do is boot to the CD and run GParted.

Maybe worth a try?

BACKUP YOUR DATA !!!!!!

---

### Post by leo_m on 2006-06-24
Maybe I missed it, but which partition type do you have - FAT32 or NTFS?  Which version of Windows are you running?  Do you have Norton software to do the needful (defragmentation)?

---

### Post by aysiu on 2006-06-24
[QUOTE=bodhi.zazen]
3. Several software tools will do this, all cost $$, none are guarenteed not to toast your windows partiton. Try partition magic or a Google search.[/QUOTE] GParted and QTParted are unreliable, but I've had no problems with the DiskDrake partitioner that appears on the PCLinuxOS live CD, and it costs no money at all--just bandwidth and a blank CD.

---

### Post by bodhi.zazen on 2006-06-26
Aysiu:

I should have specified Windows software to resize a NTFS partition are all non-free.

I agree with your assessment of GParted as I have had problems as well.

I was not awware PCLinux woould re-size a NTFS partition, thank you.

I did mention Xandros which, as I said, I have used to re-size a windows partition.

The fundimential problem may be with fragemntation of the NTFS partition, although I am not sure this matters.

---

### Post by aysiu on 2006-06-26
Ah, good point. But you don't have to have Linux installed to resize a Windows partition with Linux.

You can just download a PCLinuxOS live CD and resize an NTFS partition... for free.

Every partition program I know of can resize NTFS. The only issue with GParted and QTParted is the reliability issue. *Theoretically* they can resize NTFS. In reality, they don't always work... for anything (not just NTFS).

And, yes, defragmenting NTFS beforehand is a good idea, regardless of what partitioning program you use.

---

