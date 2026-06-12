---
title: "Installing Jaunty on PC with RAID 5 installed for XP. Need help!"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by GARoss on 2009-04-10
This is what I'm trying to do;
[I][https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Ubuntu 8.10 (Intrepid Ibex) Installation

With Intrepid, installing to a fakeraid has never been easier:
Method 1

According to the latest FakeRAID spec, Intrepid users can now install directly to SATA RAID with no additional setup or configuration required. This is is not yet supported in the Ubiquity graphical installer so you must use the **Alternate Install CD. The installer will prompt you to activate the RAID partitions, which will make them available to the partitioner and allow you to continue with the installation as normal.**[/I]

Using the Alternate Install CD for Jaunty beta, I never see any reference to *"The installer will prompt you to activate the RAID partitions..."*. I did read all the F1-F6 notes but no reference to RAID. Is this an auto detect? When I got to partitions page, all seemed like a standard installation. My understanding of RAID 5 is some boot data is installed on all 3 HDs. Is this correct or has something changed in Jaunty? I don't want to screw-up my computer!
Any ideas?

---

### Post by nanog on 2009-04-10
fist of all, ubuntu will not boot off of fakeraid raid5. /boot needs to be a standard partition or raid1. fake raid partitions need to be individually activated when using the alternate installer. 

are you sure that you do not have hardware raid5? is the array mountable from the live cd? the kernel will recognize *some* hardware raid and install fine.

---

### Post by GARoss on 2009-04-10
> **nanog said:**
> fist of all, ubuntu will not boot off of fakeraid raid5. /boot needs to be a standard partition or raid1. fake raid partitions need to be individually activated when using the alternate installer. 

are you sure that you do not have hardware raid5? is the array mountable from the live cd? the kernel will recognize *some* hardware raid and install fine.

I searched the internet & found a manual for the Gigabyte GA-7AVXP.You are correct; it is not RAID 5! The MB supports RAID-0 & 1 only; my mistake. I can say that My Computer (XP) recognizes all 3 HDDs as separate; NOT combined, which lead me to believe it was RAID-5. I'm checking Gigabyte support for software to check what type is installed.
Will the standard Live CD install with RAID-0 or 1?
Thanks

---

### Post by nanog on 2009-04-15
Will the standard Live CD install with RAID-0 or 1? 

The standard cd will recognize hardware raid supported by the kernal but will not automatically install fakeraid or lvm. Its likely that your motherboard has some form of software raid. Typically this firmware software raid is not recognized by linux and its recommended that use linux mdadm software raid. This option is available upon install in the alternate cd.

Do not use RAID0 -- it increases the chance of failure 2-fold. 

RAID1 mirrors drives. I often use RAID1 for / on my ubuntu boxes. Currently you do need to use the alternate CD but its *really* easy:

[http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1](http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1)

Thankfully this RAID mess will disappear with brtfs.

---

### Post by GARoss on 2009-04-16
> **nanog said:**
> Will the standard Live CD install with RAID-0 or 1? 

The standard cd will recognize hardware raid supported by the kernal but will not automatically install fakeraid or lvm. Its likely that your motherboard has some form of software raid. Typically this firmware software raid is not recognized by linux and its recommended that use linux mdadm software raid. This option is available upon install in the alternate cd.

Do not use RAID0 -- it increases the chance of failure 2-fold. 

RAID1 mirrors drives. I often use RAID1 for / on my ubuntu boxes. Currently you do need to use the alternate CD but its *really* easy:

[http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1](http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1)

Thankfully this RAID mess will disappear with brtfs.

All I can say is I was successful installing with the standard CD on what was old F: 200Gb. Everything dual boots with XP & it is very fast. I have noticed one glitch that might have something to do with converting ext3 to ext4 after the install process; mouse froze & had to push the reset button. This hasn't happened since.
Ext4 with swap wasn't an option with the manual install. I was trying to use manual partition, select 50Gb for ext4 of the 200Gb HDD & set swap, too. But, it was one or the other (could be I didn't understand how to use this properly but no help at the time). I had to backup to the previous menu, select F: for the install which it automatically partitioned swap & ext3 without a ext4 option.
As to RAID, I'm really confussed! Gigabyte says it is RAID-0 & RAID-1 configurable. But, my 2- 120Gb HDDs are not combined into one 240Gb HDD so it's not RAID-0. And, all 3 HDDs are completely independant of each other. The only thing I've encountered is the 2- 120Gb HDDs MUST be plugged in for XP to boot at all so something is going on there.
But, as long as Ubuntu works, I'm happy.
Thanks

---

### Post by nanog on 2009-04-18
sound like you have supported hardware raid -- kernel just automagically recognizes it.

---

### Post by marlberg on 2009-04-23
> **GARoss said:**
> All I can say is I was successful installing with the standard CD on what was old F: 200Gb. Everything dual boots with XP & it is very fast. I have noticed one glitch that might have something to do with converting ext3 to ext4 after the install process; mouse froze & had to push the reset button. This hasn't happened since.
Ext4 with swap wasn't an option with the manual install. I was trying to use manual partition, select 50Gb for ext4 of the 200Gb HDD & set swap, too. But, it was one or the other (could be I didn't understand how to use this properly but no help at the time). I had to backup to the previous menu, select F: for the install which it automatically partitioned swap & ext3 without a ext4 option.
As to RAID, I'm really confussed! Gigabyte says it is RAID-0 & RAID-1 configurable. But, my 2- 120Gb HDDs are not combined into one 240Gb HDD so it's not RAID-0. And, all 3 HDDs are completely independant of each other. The only thing I've encountered is the 2- 120Gb HDDs MUST be plugged in for XP to boot at all so something is going on there.
But, as long as Ubuntu works, I'm happy.
Thanks
 
It sounds like you did not set up the raid properly in the BIOS.  In order for the RAID to be recognizable as a raid you must enter the BIOS and set up the disks in the appropriate area per your Motherboards manufacturers instructions first.  You will need the manual for your motherboard to do this and you must follow the instructions on setting up a hardware raid precisely in order for any OS to recognize the disks as member disks.  
 
Unless you have a screen at boot that tells you that you have such and such a disk and such and such another disk as member disks of an RAID array of whatever RAID Level then you will not have a raid array volume available to the OS.  If Windows sees the three disks as 2 member disks plus one spare and you extended a stripe set (RAID 0) across the 2 member disks in windows then you created a fakeraid at the OS Level and would need to break that array and re create it at the motherboard/device level (aka NOT in in the OS ) through the BIOS.  Then if it is recognized by Ubuntu you are good to go.  If not you hardware may not support the RAID level you are attempting to create properly or it may need the mdadm utility
 
HTH

---

