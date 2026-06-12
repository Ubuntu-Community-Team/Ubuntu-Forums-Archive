---
title: "Need disk partition space advice"
date: 2016-05-14
forum: Installation &amp; Upgrades
---

### Post by abhimanyu0003 on 2016-05-14
Hi, I'm using a laptop with 1TB HDD running Windows 10. I'm about to install Ubuntu 16.04 on it and dual boot. I'm wondering how much disk space shall I give to both OSes because I want to keep them both on the same partition (C drive).

My aims:
[LIST]
[*]Windows boot shouldn't slow down.
[*]If there's a safety threshold (because I've seen at some place that Windows System Restore needs at least 50GB free space or something) of memory size for Windows C drive, I want to keep a healthy margin above that size.
[*]I don't want to compromise Ubuntu by giving all importance to Windows.
[/LIST]

My framework:
[LIST]
[*]My personal files and data are all stored in drives other than C drive. Big software like Maya and Adobe MasterCollection and games are not installed in C drive.
[*]The C drive is 99.9GB and 49GB is free right now.
[*]Even with Ubuntu, I'll store my data on those other drives (like B for bulky software, A for personal files, D for movies, etc.).
[/LIST]

My question:
How much space shall I allocate to both OSes looking at all this information?

---

### Post by jim_deadlock on 2016-05-14
For various reasons it's a good idea to install Ubuntu on 2 partitions: / (system) and /home (data) - Drive letters are only used on Windows, we don't have them over here, we just use paths for everything.

20G is more than enough for the Ubuntu system, and the rest you can leave for your Win system. You can then put your Ubuntu /home partition on your separate data drive. To achieve this, the best thing to do is run a Live DVD and fire up Gparted. Create a 20G ext4 partition on your system drive and a swap partition to match the amount of RAM you have, and another ext4 for your /home on the other drive. Then during install when you're prompted where to install select 'something else' and set the 20G to / and the other to /home and also the swap. Note: make sure you select the system drive for GRUB (on the same screen). GRUB overwrites the Windows MBR so it's a good idea to have a recovery CD handy just in case anything goes wrong and you need to reinstall MBR.

Your Windows won't slow down in any way because when you dual boot you are not sharing any resources at all with the other OS.

Your motherboard probably has 2 boot modes, UEFI and BIOS. Make sure you use the same method for both or you could run into problems.

---

### Post by grahammechanical on 2016-05-14
> Windows boot shouldn't slow down.

Then forget about dual booting with Linux. Microsoft decreased the Windows loading time by putting Windows into hibernation instead of shutting down. And unless you 

> In your firmware, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows 8, also [disable Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").

you will not successfully dual boot with Linux. Instead you should think about installing Ubuntu in a virtual machine. There are other things we must do to get a successful install of Linux dual booting with Windows 8/10

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The Linux installer (Ubiquity) will take that 50 GB of unallocated space and create 2 unequal partitions out of it. One for Ubuntu with Home as a folder. And one for Swap.

Regards.

---

### Post by jim_deadlock on 2016-05-14
I dual boot Ubuntu and Win10 with fast boot, it works fine.

The only issue if you want to keep fast boot is to make sure you never give yourself write access to the Win partition while in hibernation from Ubuntu because you can mess it up.

If he swallows up the entire spare 50G then his Windows system partition will have no free space. 15-20G for the Ubuntu / only will leave plenty of free space for both.

---

### Post by Bucky Ball on 2016-05-14
*Thread moved to **Installation & Upgrades**.*

In Linux, partitions are called by disk and partition on disk. SDA1 is disk 1, partition 1. Therefore, sdb5 would be disk 2, partition 5. sda is disk one, sdb is disk two. You say C: drive. It is not a drive, it is a partition, and it would be sda something, probably. ;)

Secondly, and most importantly, Windows and Ubuntu go on separate partitions, not the same one. 

The only way to make your Win partition any smaller would be to delete some of what's in it or move it to another drive/partition or defragment it. Either way, defragment it two or three times (or use a more efficient defrag software than the Win one) then see how much free space you've got there then shrink the Win partition leaving 15-20Gb. You should really only have the operating system in there if you've got other storage drives.

Let's be theoretical and say you have 49Gb of free, unpartitioned, unallocated space (not 49Gb left inside the Win partition). You are going to need to create a Ubuntu partition, which will take up maybe 25Gb, and a /swap partition, 2Gb or the same size as your installed physical RAM if you intend to hibernate in Ubuntu. 

Do you know whether Windows is installed using UEFI or in legacy mode? Can you get to the BIOS and check? Whichever it is installed in, Ubuntu must be installed the same way. 

Download the [Ubuntu ISO from here]("http://www.ubuntu.com/download/desktop"), create a USB or DVD of it, boot from that and 'Try Ubuntu'. All working well and you like it, hit the 'Install' icon on the desktop.

Best to select the 'Something Else' option during install. Follow your nose until you get to the partitioning section [then check here]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352"). 

If you create two partitions with the sizes mentioned during installed using the mountpoints 

/
/swap [swapspace]

... this will assume you store all your personal data on another partition or drive other than the partition you are installing Ubuntu on (as there is only 15Gb left after install). There are options for how you go about this.

There's food for thought. Let us know when you get stuck or if you have questions and good luck. :)

* Just a note, if you get this far, during install you will be asked whether you want third-party drivers and updates installed during OS install. Decline as this is known to cause problems for some people and both can be done later. This also speeds up the install. ;)

---

### Post by abhimanyu0003 on 2016-05-14
Can someone please do it remotely for me? Is running Teamviewer possible between boot sessions? Because reading all this makes me dizzy and now I feel like whatever I do will brick something... Or perhaps a condensed bulleted list explaining everything I need to do after downloading the ISO file would be better. Thanks.

---

### Post by Bucky Ball on 2016-05-14
Can I try to put it more simply? 

Windows is installed on a partition on a drive. You want to install Ubuntu on another partition on that drive, not inside the Windows partition. That may be where part of the confusion is happening? To install Ubuntu you need free space on the disk, not free space inside a partition on the disk, i.e. the Windows partition.

[LIST=1]
[*]Boot into Windows disk management (from memory), defragment the partition you are intending to shrink, which would be C:, two or three times.
[*]See how much free space is left on that partition once you've done that. If you need to, shrink it leaving about 15Gb free space *inside that partition*.
[*]You need about 20Gb to install Ubuntu (if you are going to install your personal data on another drive), which means you need 20Gb free space available on the *drive*, **not** inside the C: or Windows *partition*. Ubuntu needs to be installed on its own partition using a filesystem Win doesn't understand (ext4).
[/LIST]

Do you now have 20-25Gb at least free, unallocated space on the *drive*, not inside a *partition*? If not, rethink what you've done and/or let us know what that was and what's happening. 

While you are booted into Win, switch off fastboot or hibernation, guessing that depends on which version of Win you are using and others have commented on that. 

The next step is to download the Ubuntu ISO from the link in the previous post and create a bootable DVD or USB from that. For USB, try the [Pendrive page]("http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/"), [UNetbootin]("https://unetbootin.github.io/") or [Rufus]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") I hear works though I've never used it. For DVD I guess you'd use whatever your disk burner calls 'Burn disk image'. 

If you get that far, great! If not, still great, just tell us where you got stuck and what is now holding you up. ;)

* I just re-read your first post. You will need to shrink the Win, or C: partition, at least, say, 30Gb, depending on the eventual size of your /swap partition, to leave free space to install the ubuntu / and /swap partitions (this is if you have no free space anywhere else on the drive). As you will be keeping personal data on other partitions, that makes it easier. 

Yes, there is a learning curve, but it gets easier. :)

---

### Post by grahammechanical on 2016-05-14
Correct me if I am wrong.

You have one physical drive on that machine with a size of 1 TB = 1,000 GB. You have 4 Windows partitions/drives - A, B, C, D. How much space do all those partitions take up? 1,000GB? Maybe. The C partition (Windows 10 Operating system) is 99.9 GB with 49 GB free space. And you want to keep it that way.

So, you need to create space for Ubuntu & its data files by shrinking A or B or D. Correct? So, the first step is to create space for Ubuntu. I would advise defragging all the Windows partitions and to do it more than once and to use a Windows utility to do it. And restart Windows each time so that it can run a disk check.

The second step is to use a Windows Utility to resize one of those Windows partitions (A, B, D) so that there is sufficient unallocated space behind it to install Ubuntu in.

When you get that far we can discuss what to do next. And you have to make decisions. 

a) Do you want to keep the installation of Ubuntu simple? Then follow the guidance in that Ubuntu Wiki about fast start up and loading the Ubuntu installer in UEFI mode and chose Install Alongside when the Ubuntu installer asks you to make a choice.

b) Do you want to keep a fast loading time for Windows? That complicates dual booting and you will need advice on how to switch between Windows & Ubuntu with Windows fast startup on. You will have to accept that with Windows 10 in hibernation it is not possible to access Windows partitions/drives from Ubuntu. Try to do that and we get a warning that the partition/file system is in an unsafe state.

c) Do you want more than 2 Ubuntu partitions? If we chose the Install Alongside option the installer will automatically create a Ubuntu partition & a swap partition. If we want to put Home on a separate partition or have a separate data partition, then we select the Something Else option and things are more complicated.

Make a decision and then we can give advice relevant to that decision.

How to burn a DVD on Windows

[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)

How to create a bootable USB stick on Windows

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Installation instructions

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Do **not** select the Erase disk & install Ubuntu option. You will loose everything on that hard drive. If you do not see a Install Alongside option it could be because you have not created unallocated space for Ubuntu.

Regards.

---

### Post by abhimanyu0003 on 2016-05-14
> **Bucky Ball said:**
> 
Windows is installed on a partition on a drive. You want to install Ubuntu on another partition on that drive, not inside the Windows partition. That may be where part of the confusion is happening? To install Ubuntu you need free space on the disk, not free space inside a partition on the disk, i.e. the Windows partition.

[LIST=1]
[*]Boot into Windows disk management (from memory), defragment the partition you are intending to shrink, which would be C:, two or three times. 
[*]See how much free space is left on that partition once you've done that. If you need to, shrink it leaving about 15Gb free space *inside that partition*. 
[*]You need about 20Gb to install Ubuntu (if you are going to install your personal data on another drive), which means you need 20Gb free space available on the *drive*, **not** inside the C: or Windows *partition*. Ubuntu needs to be installed on its own partition using a filesystem Win doesn't understand (ext4). 
[/LIST]

Do you now have 20-25Gb at least free, unallocated space on the *drive*, not inside a *partition*? If not, rethink what you've done and/or let us know what that was and what's happening. 


Yes, I think that's where the confusion is. I'm sorry for sounding like a total noob at this but I really don't understand the difference here. So you're saying that the drive is the physical HDD. And a partition is the space allocated to Windows system files. Understood. But my whole HDD is divided into drives, no space is left outside of drives. The four drives make up 100% of my HDD space, therefore what's the difference between the two?

You want me to install Ubuntu system files in the C drive, and not inside the Windows partition. What is the Windows partition apart from the C drive? The group of folders belonging to Windows (Program Files, Users, Windows, etc.) make up the partition? Whatever space is left outside of Win's reach is the rest of the drive?


> **Bucky Ball said:**
> 
While you are booted into Win, switch off fastboot or hibernation, guessing that depends on which version of Win you are using and others have commented on that. 


Done already.

> **Bucky Ball said:**
> 
The next step is to download the Ubuntu ISO from the link in the previous post and create a bootable DVD or USB from that. For USB, try the [Pendrive page]("http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/"), [UNetbootin]("https://unetbootin.github.io/") or [Rufus]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows") I hear works though I've never used it. For DVD I guess you'd use whatever your disk burner calls 'Burn disk image'. 

If you get that far, great! If not, still great, just tell us where you got stuck and what is now holding you up. ;)
Downloaded, burned the ISO into a pen drive first using UNetBootin and then using Win32 Disk Imager. Both the times I got errors. I think that's not relevant here but I'll mention it anyway.

The error: So basically what happens is I restart with the flash drive plugged in. I choose UNetBootin on the blue screen where Windows asks me to choose which OS to boot. I choose UNetBootin and a box of error opens up. That box isn't important.

I burn it using Win32 Disk Imager. I choose Other Options > Boot from EFI USB drive. GRUB opens, I select Try Ubuntu (also tried Install Ubuntu and Repair Defects) to get another error. Ubuntu tries to boot, the classic Ubuntu loading screen (five dots under Ubuntu logo) appears. But after a while I get hardware errors like "error opening usb device 'descriptor' file" and something that goes like no LiveCD media channel found.

Ubuntu keeps trying to load up, but the same error message comes up in the terminal shell every 30-40 seconds, never stopping. I have to cold reboot. I tried changing USB ports, but didn't try another pen drive. I think this error part isn't relevant right now because I haven't still tried all possibilities: I'll use another pen drive in morning (3AM here) and I'll download a fresh copy of Ubuntu 16.04. The ISO I have is taken from a friend and it might be problematic. Still it'd be cool if you could throw some light on the matter.

Anyway, I'm off to bed. Will check back in like 8-9 hours.

---

### Post by yancek on 2016-05-14
Microsoft uses the terms 'drive', 'partition' and 'volume' interchangeably.   Linux users refer to 'drive' as the actual physical hard drive.  A hard drive may have only one partition which was common for older versions of windows which used up all the space on the physical drive.  Newer versions of windows generally have more than one partition.  So what you refer to as the 'C:\' drive can be both a physical hard drive and a partition if the partition takes up the entire drive.

> And a partition is the space allocated to Windows system files. 

A partition is a part of the hard drive.  The drives can be divided into numerous partitions or the entire drive can be one partition.  A partition can have system files for any operating system or it can be simply a data partition.

> But my whole HDD is divided into drives, no space is left outside of drives. 

No it isn't.  It's divided into partitions.  You need to use Disk Management (after defragmenting) to find which is the largest partition and shrink it.  That way you will have unallocated free space outside your partitions on the hard drive.

> You want me to install Ubuntu system files in the C drive, and not inside the Windows partition

No.  If you do that, Ubuntu won't run as you cannot install any Linux on a windows filesystem and have it work.  Installing windows on a Linux filesystem of course, will not work either.  As pointed out above, you need to shrink windows and create space "outside" your windows partitions which is referred to as "unallocated" or "free" space.

If you are having difficulty with the concept of drives/partitions, the link below gives a fairly thorough and basic description.

[http://www.howtogeek.com/184659/beginner-geek-hard-disk-partitions-explained/](http://www.howtogeek.com/184659/beginner-geek-hard-disk-partitions-explained/)

Since you are using windows 10, you probably have a UEFI system so it would be a good idea to read the link below on dual-booting windows and Ubuntu UEFI.  If windows is UEFI, Ubuntu must also be UEFI.  You need to determine this before beginning and how to do that is explained at the link.  It is possible to have windows 10 as an MBR install but if it was pre-installed, it is almost certainly UEFI.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Bucky Ball on 2016-05-15
Your whole disk is a disk. It has three partitions on it, not drives!!! Windows is on PARTITION C:, nothing to do with being on a drive, unless you mean that partition C: is on a hard drive. 

You are calling them drives. On a drive??? They are not drives, they are partitions on the drive. You need free space, no partitions on it (not c, d, e or anything else and NOTHING to do with Windows or the Windows PARTITION) to create a partition on during the install of Ubuntu. In fact, you will be creating two: a 20Gb root partition and a 2Gb /swap partition. :D

You'll need to shrink one or your existing PARTITIONS on the DRIVE to install Ubuntu. Get it?

Just to drive it home: You are talking about the C: partition, not the C: drive. :D

* For instance, take a look at this:

sda       8:0    0 298.1G  0 disk 
&#9500;&#9472;sda1    8:1    0   1.5G  0 part 
&#9500;&#9472;sda2    8:2    0    40G  0 part 
&#9500;&#9472;sda3    8:3    0     1K  0 part 
&#9500;&#9472;sda4    8:4    0  10.9G  0 part 
&#9500;&#9472;sda5    8:5    0    14G  0 part 
&#9500;&#9472;sda6    8:6    0 158.4G  0 part /mnt/storage
&#9500;&#9472;sda7    8:7    0   3.9G  0 part [SWAP]
&#9500;&#9472;sda8    8:8    0  14.7G  0 part 
&#9500;&#9472;sda9    8:9    0  14.7G  0 part /mnt/Misc
&#9500;&#9472;sda10   8:10   0  15.3G  0 part 
&#9492;&#9472;sda11   8:11   0  14.9G  0 part 
sdb       8:16   0 111.8G  0 disk 
&#9500;&#9472;sdb1    8:17   0  19.7G  0 part /
&#9500;&#9472;sdb2    8:18   0     1K  0 part 
&#9492;&#9472;sdb5    8:21   0  15.4G  0 part

That's my set up. It has a lot of entries, but don't worry about that. See at the end of each line? The disks are marked and so are the 'part', partitions. sda2 is my Windows partition in the first drive, sda. 

The 14Gb partitions on sda are Ubuntu installs, yes, three of them, and sdb1 and 5 are on the second drive and also Ubuntu installs. ;)

---

### Post by abhimanyu0003 on 2016-05-15
Thank you both, now my confusion about partitions and drives is clear. I'll follow the step by step method you told me now.. :)

Btw here's my Disk Management. I will defragment C couple times. Then I'll shrink C:. Then I'll create another partition from the space that is free (is it visible in here?).

Also, my A drive has 120GB free space, so can I take 30GB out from here (shrinking A) and create two partitions from this space for Ubuntu? 26GB for /home and 4GB for swap right? I have 4GB RAM.

---

### Post by Bucky Ball on 2016-05-15
> **abhimanyu0003 said:**
> 
Also, my A drive has 120GB free space, so can I take 30GB out from here (shrinking A) and create two partitions from this space for Ubuntu? 26GB for /home and 4GB for swap right? I have 4GB RAM.


Most definitely you can, and the defragging then shrinking is exactly the plan. ;)

Only two points: Windows can't create a partition to install Ubuntu to so once you've shrunk whatever partition, leave the space it leaves as free space and create the partitions during the 'Something Else' section of the install in that free space. (See the link to a 'Something Else' install in my earlier post.)

The other option is, once you get to a desktop from 'Try Ubuntu' prior to install, you can launch an app called Gparted and create the partitions you intend to install to there. It might make things clearer when you reach the partitioning section of install. Be careful either way. Just remember, DON'T go near any already existing partitions or any marked marked 'NTFS'. They belong to Windows and shouldn't be touched during install at least. 

Just a final note on that point: Always resize the Win OS partition with Windows tools, Ubuntu partitions with Linux tools. 

Secondly, unless you are intending to hibernate, 2Gb is fine for the /swap partition. 4Gb doesn't hurt either. Entirely up to you there. ;)

Sounds like you've got it now so off we go!

FYI, in Ubuntu, among other tools, we use Gparted for disk/partition management. I've attached a screenshot of my sda drive. Take note: all the NTFS filesystem partitions, apart from sda9, the /Misc partition, belong to Windows. The /Misc partition is for sharing data between Win and Ubuntu (as Win doesn't read EXT4 filesystem, but Ubuntu reads NTFS).

(PS: You can compare the attached screenshot of sda with the terminal output for sda I posted earlier. And PPS: good on ya for hanging in there with this. Yes, there's a learning curve but, for me and many others, you can be richly rewarded! After all, I for one didn't plop myself down in front of my first Win machine and know what I was doing, either. ;))

---

### Post by abhimanyu0003 on 2016-05-15
> **Bucky Ball said:**
> good on ya for hanging in there with this. Yes, there's a learning curve but, for me and many others, you can be richly rewarded! After all, I for one didn't plop myself down in front of my first Win machine and know what I was doing, either. ;))

I really appreciate all the help I got from here! Thanks again. I'll install Ubuntu soon and if I run into any problems I'll use these forums once more :D

---

### Post by Bucky Ball on 2016-05-15
If you need no further help, please mark the thread as 'solved' using 'Thread Tools' at top right or the link in my signature if you get stuck. Good luck.

---

