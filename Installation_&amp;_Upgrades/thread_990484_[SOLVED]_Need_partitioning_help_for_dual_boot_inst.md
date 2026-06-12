---
title: "[SOLVED] Need partitioning help for dual boot installation"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by eljay0 on 2008-11-22
Hello,
Well, I decided to take the plunge and give Linux a try and Ubuntu looks promising. :)

I need help with partitioning choices in the installation wizard.
Here's my current PC configuration with drive letters and partition names:
HDD #1 (120GB)
>> Local Disk (C: ) 61GB - Windows XP installation
>> Linux (E: ) 52GB - empty NTFS partition

HDD #2 (300GB)
>> Data (D: ) 127GB - empty NTFS partition
>> Data2 (F: ) 151GB - empty NTFS partition

I would like to have a dual boot machine with WinXP and Ubuntu. I would like to keep both operating systems on the first HDD. So, keep WinXP on C: and install Ubuntu on E:
Then I would use the second HDD for data and files.

However, in the installation wizard, I get to partition choices and I only have a choice of selecting guided partitioning to install Ubuntu to the first partition on the second HDD. Basically, it's only showing "hdb1" and "hdb5" as first choice.
The second choice is to use entire disk, which would wipe the XP installation and reformat the whole first HDD.
The last choice is manual partitioning, but I don't know how to partition the disks correctly to achieve my objective of dual-booting both OSs from the first HDD.

Can someone please walk me through selecting the right partition choices in the manual wizard? I can see all of my current partitions as follows:
hda: hda1 and hda5
hdb: hdb1 and hdb5
All are formatted as ntfs.

Do I need to format the hdb5 as ext3 and then Ubuntu will install on it?

Thanks!

---

### Post by Ducatiboy Stu on 2008-11-22
What it would be easiest to do is to delete your second partition, you could use windows or the live-cd start-up disk to do this using
the partition editor on the live cd ( I would use the live-cd as it will save time and it can all be done in one operation )


Then when you get to installing Ubuntu from the live CD, select guided, and you should see a 52Gb free un-formated space, select this ( you will be asked/need to format it in Ext3 ) 

Then just let it do its thing...

dot worry about how the drive partitions will be labeled, the installer will sort it out for you. If you have had previous deleted partitions, they will be kept in the partition table and new partitions will be assinged the next letter...ie it could end up as hda7

---

### Post by eljay0 on 2008-11-22
Thanks for the quick reply.
I deleted that second partition (Linux E:) on the first HDD.

However, when I go through installation, again, it's only giving me choice of Guided to resize my partition on the second hard drive. Why cannot I select first drive?
Here are my choices in the partition section of the install wizard:

1. Guided - resize SCSI2 (0,0,0), partition #5 (sdb) and use free space
It shows this: 
Before: /dev/sdb1 (45%) /dev/sdb5 (54%)
After: /dev/sdb1 (45%) /dev/sdb5 (0%)  Ubuntu 8.10 (53%)

2. Guided - use entire disk
   - SCSI1 (sda) - 120GB
   - SCSI2 (sdb) - 300GB

3. Guided - use the largest continous free space
It shows:
Before: /dev/sda1 (54%)  Free Space (45%)
After: Ubuntu 8.10 (100%)

4. Manual

-----------
Why isn't there an option to use the free space on sda?
Do I need to go into "Manual" and then create new partition in the free space on sda? If yes, what should I choose as options? IS this Primary or Logical, location Begin or End, and use as Ext3? Anything to choose in the mounting point?

Thanks!

---

### Post by Ducatiboy Stu on 2008-11-22
have you used the partition manager on the live-cd...??

System-> Admin -> Partiton editor


It will give a nice easy grahpical pic

Go into manual and create a new partition on free space sda, ext3.  It will be a logical volume, but the installer will work everything out for you



What version of ubuntu are you installing, because 8.10 ( Intrepid ) has a nice graphical install partitioner

---

### Post by eljay0 on 2008-11-23
Thanks! That worked. I just needed a visual I guess. :)
I am typing this from Ubuntu 8.10.  :)

So far, I really like this OS. I couldn't believe that it detected my USB wireless adapter and connected to wireless network in 2 clicks! Wow! No installation software wizards like WinXP.

I'll be back here for more, but hopefully, not under Installation section anymore!

Thanks again.

---

