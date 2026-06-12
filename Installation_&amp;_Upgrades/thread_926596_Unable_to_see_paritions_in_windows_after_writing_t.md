---
title: "Unable to see paritions in windows after writing to disks from liunx"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by lilpaul on 2008-09-22
Basically, i've recently install linux and im pretty new to it.

I have 3 disks in my system, 1 for O/S and the other 2 for DATA.

I wipped my o/s drive and installed ubuntu hardy heron on my OS drive.  In Ubuntu i was able to see my other drives and partitions and have written data to both disks.

Later i decided I wanted a dual boot system, so wiped my o/s drive again and installed XP, then installed ubuntu again.

The problem i have is that i can see the partitions in ubuntu but not in XP.  The partitions on the DATA disks are all NTFS.

How can i make these visiable again in XP, have i damaged the paritions in any way by writing to the disks in ubuntu and can i get my data in XP.  

Any help would be appreciated

---

### Post by prshah on 2008-09-22
> **lilpaul said:**
> 
The problem i have is that i can see the partitions in ubuntu but not in XP.  The partitions on the DATA disks are all NTFS.

How can i make these visiable again in XP, have i damaged the paritions in any way by writing to the disks in ubuntu and can i get my data in XP.  

Are any of the "missing" partitions on SATA drives? Are all three drives detected in XP? Check with XP's disk management utility: Click Start-Run```
diskmgmt.msc
``` (You can post a screenshot of this window here if you cannot understand it. Maximise to full size first.)

If you cannot find your SATA drives, XP (prior to SP3) has trouble with those since SATA drivers are not available in XP SP2 installation files and below. Now you can:

a) Upgrade your XP to SP3
b) Install the SATA drivers that come with your motherboard, if you have any.
c) Check in BIOS for SATA options such as "Native Mode", "Legacy Mode", "IDE Compatible mode", etc. (The option varies from BIOS to BIOS, so I cannot be more specific). Note that this _may_ cause XP to become "unbootable".

---

### Post by lilpaul on 2008-09-22
Thanks for gettin back to me.

Im away till the weekend but will have a look when i get back.

Hopefully it will just be a matter of it not having the sata drivers installed.  I didn't check that i could see the partitions when i had SP3 installed only SP2.

I'll give it a whirl when i get home.

---

