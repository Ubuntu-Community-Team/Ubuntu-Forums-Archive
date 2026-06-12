---
title: "Finally how to triple boot with no frills at all"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by redheat on 2007-06-06
Hi everyone

 Ok I had this huge problem of how to triple boot my system from a single harddrive. I have windows xp professional, windows vista business, and Ubuntu 7.04. I looked everywhere for answer to that problem and google days and night on how to triple boot, but most guides were either done using the previous version 6.06 or none..No one actually out there did a decent noob-friendly triple boot..will noob dude and dudettes I got it and finally it working like a charm on my system, and I did it more than three times to make sure that it didn't work because of fluke of luck...Just try to bear with me..

 First of all the ingredients:

1. I have three harddrives: two 250 GB western digital harddrives, and one 320 western digital harddrive.
2. My motherboard is the famous gigabyte motherboard GA-965p-DS3/S3.This motherboard has six SATA ports. Two of these ports are controlled by a SATA controller made by Gigabyte called GSATAII and they have a purple color, and four SATA ports controlled by Intel ( the famouse ICH8 southbridge controller), and they have orange color. You can see this awesome motherboard here:
[http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2456](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2456)

 If you want to use the AHCI version you have to download drivers for it for the windows xp installation and you can do that from here: [http://kerneltrap.org/node/7582](http://kerneltrap.org/node/7582) and then from here: [http://sniping.org/2007/03/09/ichicanery8/](http://sniping.org/2007/03/09/ichicanery8/)

 Of course this is in case you're going to use SATA if you want the good old PATA way do it, it won't matter a lot.

 NOTE: of course most of you have read this warning, but it won't harm to say it again, back up all your data on other harddrives or other storage mediums before your do anything.

 Now let's begin:

1. Turne off your system. Take the power plug out, and open the case.
2. Get all of your harddrives out just leave the one which you want to install the Operating Systems on,  let's call this harddrive the "OS drive". Before you do anything go to your BIOS, and probably under ADVANCED BIOS FEATURES you'll find an option called HARD DISK BOOT PRIORITY or something similar, and go and make sure that you're harddrive is listed as number one, actually it should be since it the only one..just checking you're with me...) of course update your bios, the latest bios version for the gigabyte motherboard is F11. Also, make sure that First BOOT device is your CD-ROM or DVD-rom I mean whatever the optical medium you use.
3. Now your OS drive will be know as hd0 or sda since it the only one there.
4. You can partition the harddrive in anyway your like this is how I did mine which is 320 GB:
 a. Partition C: 80 GB for windows xp
 b. Partition D: 80 GB for windows vista business
 c. I left 30 gb of unallocated space ( that is upartitioned) for ubuntu to let ubunto do the partitioning itself
 d. Partiiton E: 140 for non-os stuff ( the usual crap we keep loading on our system) of course at them moment, I moved all my stuff out of it. 

 NOTE: as you all know the ephemeral rule which says you can not have more than four primary partitions on a single harddrive. That's absolutely true and no question about it, but who said that an extended partition was not a primary one. I discovered this from a previous install of ubuntu, when I was pulling my hair out which not many of it is left :( ,  The story was like this, I partitioned my harddrive into two primary partitions for both windows versions, which left me with only with two primary partitions left. from a previous advice I thought I had to manually partition these into two primary pertitions one for the ubuntu file system "/" and another for the linux swap, but it left me with unallocated space of a hundred and forty, but whe n I tried again this time I followed up the above partitioning system, and I was gazing at the manual paritioning system, when I right clicked on it I got the following message: an extended partition is a primary partition with the ability to create logical drives, and I found out later on if I left Ubuntu to do a guided installation on its own it would partition the filesystem into an extended partition. 

4. Of course you can partition your harddrive either using the "gparted" which is the partition manager for ubuntu which you can find it here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=125754](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=125754)  ( just download it and burn it to a CD) or you can use your windows vista partitioning manager.. Most of you who have installed windows vista before have already noticed vista partitioning manager. It did a greate job for me, just like gparted.

5. After you've partitioned, of course whatever the partition size is up to you, but leave ubuntu's space unallocated don't partition, just try my advice .

6. Now, install windows xp, and of course if you're using the AHCI SATA feature use the drivers for your controller. Remember, this is very important, The two SATA controller GSATA II and Intel need separate drives for windows xp to recognize their partition or you won't see them on your installation screen.SO make sue to press F6 quickly before you begin installing windows xp, put the floppies for the intel and the gsata drivers.

7. Now install windows xp, and after you finish the installation and you make sure that you've already made it to the desktop and its running smoothly. You move on to the installation of windows vista. Some people might tell you wait till you update your windows xp, it doesn't matter at all, I did mine without even installing the motherboard drivers. It has no effect.

8. Now install windows vista which I reckon is easier than xp and takes less time and ..looks prettier :) After you finish installing windows vista and restart your computer for the first time you will come, and even during the installation you'll come across the "OS choice menue" where you'll be prompted to choose which operating system to log into:
  1. Older versions of windows
  2. Windows Vista..

9. Just like with windows xp, after your login to vista you don't have to install anything else, just get ready to install ubuntu.

10. Now we come to installing ubuntu, of course make sure that you have version 7.04.
11. Put your live CD and restart your system now you should come to the ubuntu installation menue..choose install ubunu which will lead you to the ubuntu's desktop.

12. On the desktop click on install, this will start installation.
13. The first few steps are self-explanatory, language, time zone..etc till you come to the partition page..
14. I want you, please, to choose guided installation make use of the largest contiguous free space, not manual. If you want manual..it won't make a lot of difference because Ubuntu does get it right, and it does partition the unallocated space which you left from the beginning very successfully with no trouble at all.
15. After you choose the guided installation you'll be taken to the installation summary page which shows you the options you choose for your installation. Near the bottom right section of that page, there's an option called "Boot loader Installation device" which asks where you want to put your bootloader and it displays (hd0) leave it as it is, since this harddrive is hd0, is the first one because its the only one. now click finish to begin installation. 

 now relax, and let the system does its charm, it will partition the unallocated space and format it into ext3 and linux and of course both of these partitions will be two logical under a bigger extended partition that includes all of the unallocated space that you left from the beginning.

 Now, all things should go fine, and after you take your cd out, and restart you will come across the grub menu which will offer with many choices like:

Ubuntu 2.6.16 (generic)
Ubuntu (recovery mode)
Ubuntu memtest x86
Other windows installation:
 Windows vista (loader)

 if you chose the Ubuntu generic it will take you to ubuntu, while if you chose vista it will take you to the menu where you get to choose windows vista or "older windows versions"  the one you had before when you had only both windows vista and xp..

 Now, of course after your installation, which I assume and suppose will be very successful. Of course, during all of this, don't reinstall your harddrives, after you have settled and made sure that all of your installation are going ok. Install each drive by itself don't put all the other drives at the same time. And after that go and log in and out of each operating system installation to and check your drives. 

 Ok folks...that'll be all..
one thing, just comments and follow ups..

 Now I have a thought about it you want to install three operating systems on more than one harddrive.
 Install make sure that windows vista and ubuntu lie on the same drive, I don't know why ubuntu sees windows vista with the word "loader" next to it. But this is how I see it, and i'm no expert in linux or boot loader brouhaha thing, I thing windows vista boot loader overtakes windows xp and ubuntu sees it as the only loader there is, and that's why in the grub menu we see only windows vista as loader, sort of a shortcut to windows vista loader which in itself is a shortcut to choose vista or xp...I would thankfully appreciate anyone's notes and recommendation on this comment. That's just a simple "common sense" workout nothing solid..:)

 regards to you all and good luck wth your new triple boot os system
redheat.

---

### Post by Elrohir on 2007-06-07
yeah, well... some people may kill me for this but you can sacrifice GRUB and use Vista boot loader... [Here's the tutorial]("http://www.hevnikov.com/blog/2006/11/13/triple-boot-xp-vista-ubuntu-with-single-boot-screen/"), yes I know it says 6.10 (Edgy) but the process of installing Ubuntu is the same...

---

