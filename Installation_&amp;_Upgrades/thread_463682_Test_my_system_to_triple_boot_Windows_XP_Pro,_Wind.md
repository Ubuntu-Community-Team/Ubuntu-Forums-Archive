---
title: "Test my system to triple boot Windows XP Pro, Windows Vista, and Ubuntu 7.04"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by redheat on 2007-06-03
Ok guys/gals

 Here's the deal..I'll let you, test and try to boot a triple OS composed of Windows XP Professional, and Windows Vista Business, and Ubuntu 7.04. and here are the details of my system:


 First of all, I have a Gigabyte GA-965P-DS3 Motherboard which comes with the famous two SATA controllers:

 1. Four SATA ports controlled by Intel's ICH8 
 2. Two SATA Ports controlled by GSATA, which is Gigabyte's SATA controller.

 Of course the above have nothing to do with my problem I just thought I should tell you about them. 

 I have three harddrives:

 1. One Western Digital (250Gb installed on one of the four SATA ports controlled by intel's) 
 2. Two Western Digital (320, 350 Gb each) installed on the other two ports controlled by Gigabyte.

 The 320 GB have been partitioned into the following scheme:

 1. partition C: 80 Gb for windows XP Professional
 2. partition E: 80 GB for Windows Vista Business
 3. Partition F: 30 Gigabyte: left for Ubuntu 7.04
 4. partition G: 130 Gigabyte left for non-os stuff.

 I have already installed Windows XP, and Windows Vista, and I have set the drive containing them to be the first one to boot from in the BIOS.

 Now comes the big problem when installing Ubuntu 7.04. I have already formatted and reformatted my hard drive because of Ubuntu more than 10 times in the last couple of days, and I still can't get ubuntu to run on my system:

 These are exactly the steps I follow when I install Ubuntu:

 1. I insert the Live CD, and then I go to install, choose the part about language, time zone..etc.
 2. I come to the point where I have to do a disk partiition. Ok
 3. For this option I choose "Guided install..Make use of largest continuous free space" 
 4. after leaving that page, I come to the summary page which lists all the options for my install, and there's that new advanced button near the bottom-right part of the screen when I click on it opens and it asks me where to install the boot loader, 

 If I chose hdo, in this case, I get the following error, missing Bootmanager, or No such partition.

 If I chose hd1, this is the harddrive where Ubuntu installed, I get the Grub menu but whatever I do it won't work. if I chose the Ubuntu 2.6....etc, it gives me no such partition. or error 11, if I chose Windows Vista..the answer would be missing NTLDR, if I Chose windows xp or other versions of windows I get error 11..and so forth..

 So this is what am I gonna do, I formatted the drive where I want to install the three OS into 4 partitions, 3 primary partitions, and the third one, which is left for ubuntu, I left it as an unallocated space to whatever you like with it..just tell me what to do guys...

 I have used gparted to know the names of my harddrives, of course I've forgot to mention they all are SATA drives:

1. The first harddrive, also called (hd0) or (sda) is located on one of the four SATA ports controlled by intel.

2. the second harddrive, this is the one with the 320 GB and where I want to install the three systems is installed, is called (hd1) or (sdb) and is installed on one of the two ports controlled by gigabyte. the partitions are as follows:

sdb1 is the partition where windows xp is installed
sdb2 is the partition where windows vista is installed
sdb3 is the partition where the non-os stuff exists
sdb4 ( is usually the extended partition created by ubuntu or me, if I choose manual partition, and is subdivided into)

sdb5 this is where ubuntu is installed and its filesystem is Ext3 and sdb6 where the swap file is located.

 So guys/gals, start your engine and let me have it..I'll ask you what to do in each step...

1. Step One: Should I do a manual partition of the unallocated space designated for ubuntu, or use the guided installation option under install where ubuntu makes use of the largest continuous free space. By the way all the harddrives are partitioned the only unallocated space is the one left for ubuntu of the OS harddrive, and can we call like this the OS harddrive..

waiting for your replies

regards
redheat...

---

### Post by laughing_at_you101 on 2007-06-04
ok, i'm pretty sure an os has to be on a primary partition, so what you could do is, wait until AFTER you've installed ubuntu to make the non-os partition, i'm not sure if you can have more than 3 primary partitions, but in any case, when ubuntu asks how you want to set up the partitions, do it manually, and click next, then select the third partition on the drive and format it to ext3 and mount it to /, proceed with the install, put grub on sdb, add your windows partitions to grub, proceed with the install, that shoud work, if not, i don't know, i'm fairly new to linux myself, but i know a bit on how partitions work and how the mbr works

---

