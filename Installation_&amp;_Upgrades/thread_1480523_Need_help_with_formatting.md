---
title: "Need help with formatting"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by cezar_dan on 2010-05-11
I recently had some troubles with my laptop and I will soon be re-installing Ubuntu but this time I want to make it a really clean install. Before I had a NTFS partition with my data left over from Windows that I want to format.

I want to have two partitions on it but I'm not sure what format the second should have. Should I make it NTFS again or is ext3 better?

Also, a friend wants to "zero-fill" my harddrive beforehand with a program from "Hiren's boot CD". Should I do this? Will it help with any bad sectors? Is there any risk to this?

---

### Post by srs5694 on 2010-05-11
If you won't be installing Windows on the computer, *do not* use NTFS; Linux lacks good NTFS maintenance tools, so when something goes wrong (system crash, power failure [yes, I know, laptop, but still....], etc.), the partition will be completely useless until you boot with a Windows emergency disc to repair the partition.

I recommend you create at least three partitions:


[list]
[*]**root (/)** -- Make this one 5-20GB, depending on your disk size and how much software you plan to install. The Linux system itself goes here.
[*]**swap** -- Make this at least as large as your RAM. When you suspend to disk, it will hold your RAM contents, and it will also be used to supplement your RAM if and when your memory needs grow beyond your RAM's capacity.
[*]**/home** -- This partition will hold your user files. Keeping it separate from root (/) enables you to completely wipe your Ubuntu installation and re-install without damaging your user files. Give it all the free space not already assigned to root (/) and swap.
[/list]


As this will be a Linux-only installation, you may want to consider using the [GUID Partition Table (GPT)](http://www.ibm.com/developerworks/linux/library/l-gpt/index.html) partitioning system, which has several minor advantages over the older Master Boot Record (MBR) system, including an elimination of the klunky primary/extended/logical partition distinctions, checksums to detect corruption of partitioning data, an on-disk backup of partitioning data, and names that can be assigned to partitions. These advantages are all pretty minor, though, so if you use MBR, I can't say that's a bad decision, either. Eventually you will be using GPT, since MBR can't cope with disks bigger than 2TiB (assuming 512-byte sectors; the limit goes up a bit with bigger sectors). This limitation isn't an issue with your laptop unless you're using a prototype drive from a hard disk manufacturer.

I don't see much point to zeroing out your hard disk unless you plan to sell the computer or drive, in which case zeroing it out will erase traces of potentially sensitive data that might be lurking on the disk. If you think the drive may be going south, I'd replace it rather than try to force the drive to notice the bad sectors by zeroing it out.

---

### Post by cezar_dan on 2010-05-12
Thank you, this answers almost all of my questions. Just a few minor things left since I want this install to be as close to perfect as possible:

1. Is ext3 a good format for /home or should choose another? And should it be a logical or primary (I'm thinking logical).

2. When installing Ubuntu before I always set the root partition set as a primary. Is this ok? Any other recommendations for my installation?

Extra technical data:
I have one 40 GB hard drive that I want to partition: 8 GB for Ubuntu, 1 GB Swap, 31 GB for any other data.

The zero-filling will probably be necessary since my hard drive is a bit messed up. A recent attempt at installing Windows 98 SE for more obscure programs that WINE doesn't run ended in most of my data being lost, then partially recovered (recovered the NTFS partition, but lost Ubuntu). It's probably the only way to make sure there are no more problems. A new hard drive is out of the question at the moment :(

---

### Post by narendraD on 2010-05-12
Ext3 is  a very sound and stable FS for /home and is a good choice. EXT4 may also be considered. Logical is fine for /home
If Ubuntu is the only OS then it is Primary anyway but is not necessary. Let the installer make it ext4
[srs5694]("http://ubuntuforums.org/member.php?u=1032238")'s advice on partitioning is ideal for your case and you can go ahead with it.

And Backup your data before you do anything.

---

### Post by migs73 on 2010-05-12
Hi
I was thinking of doing a similar thing (I am a bit of a noob) but wondering if I can use Gparted to set up a /home partition now, copy my current /home folder settings into it, then do a clean install with lucid onto the root partition?
Would this fall over as I would have two /home at one time?
Could I rename the partition as something else until after the install and then change the name to /home?
Once the new Lucid install was complete, how do you gain acces to /home? Does the OS just treat it as normal or would I require to do something to tell it the settings etc was not on the root partition?
Sorry for the multiple questions, I just do't want to wreck my current settings as I have Virtual box with Vista as one of the hidden folders, which makes my home folder to big to fit on any external HDD's I've got (It alone is nearly 30Gb).
 
PS I will back up all my data seperately. I am just wanting a clean install of Lucid as I have slow boot times, which I think may be caused by my having upgraded from Karmic

---

### Post by narendraD on 2010-05-13
You can use Gparted to create a Partition, but marking it /home and backing up your settings before the install is a bad idea. You cannot have 2 partitions marked /home. Backup up all data in /home, create a partition of sufficient size for home. then during the install, at the Partition page, choose manual and mark the newly created partition as /home and the existing partition that has / as /. You may format the newly created /home because you have no data on it. Once the install is complete you can copy over all backed up data to /home.

---

### Post by migs73 on 2010-05-13
Now i have hit a problem. 
My back up drive was formatted to fat32 (i think) and would not allow some of the files I wanted to backup to be copied. Thinking this was a good time to test GParted, I downsized my existing partition and created a new 50GB ext3 one to back up my settings into.
All great so far.
 Unfortunately this partition only has permissions for root, so I cannot copy anything into it. How do I log in as root and alter the permissions? Should this partition be primary or extended??

---

### Post by dino99 on 2010-05-13
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by migs73 on 2010-05-13
For the avoidance of doubt, the partition I made was on my backup USB drive not my Ubuntu one. It is this backup partition that I don't have permissions for.

---

### Post by dino99 on 2010-05-13
you can install mountmanager and set your prefs about devices and partitions as you need

---

### Post by migs73 on 2010-05-13
Thanks Dino,

I tried this but still it does not give me permission. The setting for Read and Write was set for everybody anyway. There is no set up for permissions even on the advanced tab. (NB there does seem to be permission settings on the other partition which is vfat).

Edit; I have just reformatted that partition as fat32 and copied all the data over ignoring the 'symbolic link' problem with some files. Will this cause problems when I try to copy the setting back in to the new home folders? Are they necessary?

---

### Post by migs73 on 2010-05-14
Any way just got back up and running with a clean install of lucid with a separate /home partition. My Vbox running vista was my only casualty, lots of problems when trying to run it. Just flattened that and did a re install, not to much of a problem but it takes sooooooo long to install windoze (1hr+) as opposed to the 30mins for Ubuntu (including the repartition/format of the drive).

Many thanks guys. By the way I did this to try and reduce my boot time. Was originally 1min 8s now down to about 45s. Great result.

---

