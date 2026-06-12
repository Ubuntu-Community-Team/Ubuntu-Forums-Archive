---
title: "Install, 2 partitions on disk0 already, need to shrink Win partition?"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by gencon on 2010-04-17
New user here so apologies if I've got the wrong idea...

I am going to install Ubuntu 9.10 Karmic Koala on my desktop PC which has Windows XP SP2 on it already. I want a dual boot for the time being.

In XP's Computer Management my 500 GB 'Disk 0' shows that when I installed Windows I created 2 partitions on that disk, the C drive partition of 100 GB which I created to hold only the Win XP OS and its 'Program Files' and an E drive partition of 400 GB - both partitions are NTFS.

I also have 2 more hard disks inside the PC: 'Disk 1' of 500 GB and 'Disk 2' of 1000 GB, each has a single partition, drives D and F, again both are NTFS.

Instead of shrinking the C Windows OS partition can I instead modify the E drive partition (remember that's the one on the same physical drive as the Windows C drive) to create the necessary partitions on which to install Ubuntu? In so doing I'd avoid having even to touch the Windows OS drive and limit my risk of corrupting it should things go wrong.

Alternatively could I use either of the other 2 hard disks to create the new Ubuntu partitions?

What would you all advise?

Many thanks and regards, etc.

---

### Post by zvacet on 2010-04-17
You can do it both ways.You can shrink E drive during Ubuntu installation process and install Ubuntu on unallocates space or you can install ubuntu on separate drive.In that case install grub on MBR so grub can see both OS.

---

### Post by oldfred on 2010-04-17
Depends on where you have the most free space and ease of resizing. Either way you should defrag twice before resizing.

Some users like a operating system on every drive. 
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

I tend to prefer having different operating systems on different drives with that drive's boot loader in the MBR so each drive can boot if required. Ubuntu/grub of course finds other operating systems so I make it my default boot drive in BIOS (I boot sdc). Another slight advantage of installing in another drive is you can leave the windows boot loader alone. If you install to another drive be sure to use the advanced button at the end of partitioning or else grub will still overwrite the windows boot loader in sda. They are still working on fixes/changes for where grub installs by default.

---

### Post by grifonas on 2010-04-17
> **gencon said:**
> 
Instead of shrinking the C Windows OS partition can I instead modify the E drive partition (remember that's the one on the same physical drive as the Windows C drive) to create the necessary partitions on which to install Ubuntu?

If during the installation you choose your drive E as the destination for Ubuntu, it should automatically prepare the whole partition for itself. Without you having to do anything. I did it this way on several occasions and dual boot was created automatically every time. 

Oh, and I probably should mention that your partition is not gonna be called "E" when you're installing Ubuntu. But you'll be able to easily identify it by its size.

---

### Post by libron on 2010-04-18
This is a really dumb question but I just joined the forum and I'm a total newbie when it comes to Ubuntu.  I love the way Ubuntu works running off the DVD and can't wait to get it installed on my PC so I can kiss Microsoft goodbye.

When you say install Grub to the Master Boot Record is that done using the Advanced button located at the bottom right of one of the installation process screens?  I think it's right after the screen with partition manager.  I'm really afraid of screwing up my PC and not being able to launch either OS.  Is there an FAQ that I haven't found yet that explains this?  

Thanks in advance for any help you can give me.

---

### Post by oldfred on 2010-04-18
libron and previously gencon welcome to the forums.

Libron it is considered impolite to steal someone else's thread. If you have exactly the same problem (rarely with boot configuration issues) you can add to the discussion. You should start a new thread.

I always have several liveCDs, supergrub, gparted liveCD, and one or two repair CDs and now also I have them all on my USB key. Just in case.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by gencon on 2010-04-19
Thanks for your replies everyone.

Quick reminder before my next questions, I wrote:

"In XP's Computer Management my 500 GB 'Disk 0' shows that when I installed Windows I created 2 partitions on that disk, the C drive partition of 100 GB which I created to hold only the Win XP OS and its 'Program Files' and an E drive partition of 400 GB - both partitions are NTFS."

I'm now intending to use the 'E drive partition' for my Ubuntu installation and over night copied the drive contents to another internal drive and to a USB backup drive, I can now safely delete the entire 400 GB drive contents.

Here's what I want to achieve but am not sure exactly how to go about it.

1) Create a 100 GB partition for the Ubuntu installation.

2) Create a Ubuntu swap partition, what size? I have 4 GB RAM, should the swap partition be 8 GB, more?

3) That leaves about 290 GB to make another partition, NTFS so it can be accessed by Linux and Windows XP.

I am unsure about a few things. How should I make these partitions? In Widows before the installation or during the Ubuntu install process?

What filesystem should I use for the Ubuntu partition and swap partitions? These must be formatted by Ubuntu during the install if not NTFS. But should I use NTFS so I can access the Ubuntu partition from Windows, are there any advantages or disadvantages to doing this?

How and when should I format the remaining NTFS 290 GB partition?

A couple of people who replied said to install grub in the MBR, how do I make sure this happens? Is everyone sure this is what I should do? Remember the Win OS and Ubuntu installation will be on the same physical drive, in different partitions. To be honest I am not even sure what boot alternatives exist in a dual boot Win/Ubuntu system.

Many thanks again everyone, sorry to ask so much, I am a bit afraid of mucking everything up.

---

### Post by oldfred on 2010-04-19
The manual install requires you to create the partitions in advanced so we usually do not recommend that as most do not understand partitions.

I think you at least under stand what a partition is. If you want more than the 4 primary, you have to convert one primary to extended and then can create just about any number of logical partitions inside the primary. This may require deleting the existing NTFS partition but you have your data backed up so that should be ok.

Use gparted from either the liveCD or download a gparted liveCD to make partitions & format them. Make your new 290GB NTFS partition, Make your root(/) partition and make swap 4GB same as RAM. You may want to make a /home as that is where all your Ubuntu data & settings go and then your root only needs to be 10-20GB in size. The install will ask you if you want to format the Ubuntu partitions.

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
I think she still has FAT in her scheme but now use NTGS instead of FAT,  otherwise good info:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Install karmic Screens shown
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

---

### Post by gencon on 2010-04-20
Thanks again oldfred for your reply and helpful links. Unfortunately in them and elsewhere I've found a little bit of conflicting advise, no doubt this is mostly down to the personal preferences of the writers.

Here's what I propose doing. First I'll mention that I am going to forget about the extra 290 GB NTFS partition, I'm not short of disk space on the other 2 drives so why bother complicating the issue!

500 GB 'Disk 0':

Current Situation:

Primary Partition 100 GB, NTFS, Win XP OS & Programs - already there.
Second Partition 400 GB, NTFS - data backed up (twice) and deleted already.

Proposed Partitioning Procedure:

Primary Partition 100 GB, NTFS, Win XP OS - leave completely alone.
Second Partition 400 GB, NTFS - delete partition.

400 GB now available after the primary partition to do this (in order):

a) Create 100 MB GRUB boot partition, format with ext3.
b) Create extended partition with the rest of available space.
c) Create logical partition for root, 100 GB, format with ext3.
d) Create logical partition for swap, 4 GB (size of my RAM), format with ext3.
e) Create logical partition for home, 286 GB, format with ext3.
f) That leaves 10 GB free at the end of the extended partition so in case of an emergency I can create an extra logical partition.

How does that sound? It's based on the links oldfred kindly supplied.

I have a couple of questions:

1) [https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes) suggests the 100 MB GRUB boot (primary) partition - is that a good idea, and how do I tell Ubuntu to use it? Would more space be better? 1 GB, as I have plenty of disk space?

2) Does the order of my c), d), and e) logical partitions make any difference? If so, how are they best ordered?

3) [https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes) also suggests an extra primary partition of 2 GB between the Windows partition and the small GRUB partition - possibly a 'Windows recovery partition', since I have no 'Windows recovery partition' what would be the purpose of creating this?

Many thanks again. [This is more complicated than I thought it would be.]

---

### Post by oldfred on 2010-04-21
Everyone has there own recommendations on partitioning and for every post or web site you see you will get several different versions. 

I would not recommend a separate grub partition unless you plan on booting many different operating systems and want to chainboot into them. (very advanced in my mind). I orginally created a /boot partition but converted it to a /boot/grub partition for chainbooting into my old versions of Ubuntu using old grub, with grub2 it finds all the operating systems I use - windows and versions of Ubuntu. Almost all your data will be in /home or your NTFS partitions. You will find you only use about 5GB in / (root) unless you run a db server and do not move those files to a separate data partition. I recommend 10-20GB for root.

It does not greatly matter what you do as after you start using your system you will find that it may not be optimal, but that is because each of us use our systems differently. After you have used it a while you will want to reconfigure or will be buying a new hard drive and will be changing anyway.

---

### Post by gencon on 2010-04-22
I'm not sure what happened (must have hit preview and forgotten to hit submit) as my last 'reply' thanking you is not there!

Anyway many thanks oldfred and others for all your help, it's really appreciated. My Ubuntu install went about as smoothly as I could possible expect, no problems at all, and I'm happily typing this in Karmic. :)

---

