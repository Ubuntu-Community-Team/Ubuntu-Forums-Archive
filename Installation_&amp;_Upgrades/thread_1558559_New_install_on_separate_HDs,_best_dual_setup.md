---
title: "New install on separate HDs, best dual setup?"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by Agencyman on 2010-08-22
**Full disclosure statement:** I'm nearly a complete newb on Ubuntu/Linux, I had one dual boot system a few months ago, but had to wipe that one and re-allocate the machine to another location for spouse.

The 'perfect partition" thread came close to dealing with my dilemma, but I want to get this right.

So:

New build, reformatted HDs for clean installations.  150 Gb, and 74 Gb, this small one is exclusively for Ubuntu; (it is a Raptor, and with a Core Duo at 3.5GHz, this hopefully will be a zippy Linux machine!)

[SIZE=3]I have the v10.04.01 Desktop .iso on a CD, and tried to install this morning,[/SIZE][SIZE=3] but when I got to the space allocations, it seemed to just look at the Windoze 7 drive, the 150 Gb one, and want to divide it up for dual boot.  When I tried the 'advanced' partitioning, I found I was in over my head.[/SIZE]

I might like to have a shared partition too, but that is lower on my priority list than the complete autonomy concept.
[SIZE=2]
[/SIZE] [SIZE=3]I had hoped to have a totally independent drive environment for Ubuntu, maybe even with it's own root/file system?  This would allow highly simplified separate imaging and drive upgrading for each O.S.[/SIZE]
Do any of you here know if a method been devised to allow such a total independence of the two O.S.s?

Bruce Hinton

---

### Post by confused57 on 2010-08-22
Here's an excellent tutorial for what you want to do:
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by Agencyman on 2010-08-22
"Erase and use entire disk!!!  That was so frightening that I never considered getting anywhere NEAR that button!"


Thanks for this reference, it is exactly what I was searching for.  If it works, I'll be closing out this thread very soon.

Bruce

---

### Post by oldfred on 2010-08-22
I only had / (root) and swap for several years. But with winXP I created a shared NTFS partition so I could have the same firefox and thunderbird profiles in both. Now I am in windows so little that is less important and I created a separate /data partition for sharing between different systems. 

I prefer to have smaller system partitions of about 20-25GB (I actually use only about 6Gb) and put all data into other partitions. By having several root partitions I am able to install several versions of Ubuntu and I have space to experiment if I so desire. But all my data can be easily mounted in each system.

But you just about have to do partitioning in advance and plan what partitions you will want. Then install system perhaps /home and swap into the partitions you have made in advance.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
Partitioning basics with some info on /data older but still valid by bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by Agencyman on 2010-08-22
> **oldfred said:**
> 
I prefer to have smaller system partitions of about 20-25GB (I actually use only about 6Gb) and put all data into other partitions. By having several root partitions I am able to install several versions of Ubuntu and I have space to experiment if I so desire. But all my data can be easily mounted in each system.

But you just about have to do partitioning in advance and plan what partitions you will want. Then install system perhaps /home and swap into the partitions you have made in advance.

Interesting; I think I shall place an extra partition or two on the Ubuntu Drive.  I will probably put GRUB only on this drive, use [F11] to get there; maybe a duplicate on the Windoze 7 drive later if it seems like a good idea or necessary move.

With 70Gb to start with, are you suggesting that I set aside, say, 20Gb for the Ub.O.S., and set up one or two more for data?  Could one be later configured as shared with the Windoze O.S., since they will be on different drives?  It will have to be NTFS, I think.

Once I find the order to this install, I shall surely find order in my world! :)

Thanks for this list of resources, I shall go read now.

Bruce

---

### Post by oldfred on 2010-08-22
Be sure to use the advanced button on the Ubuntu install to make sure you install grub to the Ubuntu drive. It wants to default to your normal boot drive (usually windows). Once you start booting sdb the Ubuntu drive you will find you can boot either Ubuntu or windows easily and not have to use f11 to switch. I like to keep the windows boot loader in the windows drive so that drive could be booted on its own if ever necessary.

I do not like writing into the windows system partition unless I have to for repairs, that is why I prefer to have a shared data partition. Some windows users even recommend a separate D: drive for windows so when it breaks and you reinstall your data is safe. (of course you still back it up)

---

### Post by Agencyman on 2010-08-22
> **oldfred said:**
> Be sure to use the advanced button on the Ubuntu install to make sure you install grub to the Ubuntu drive. It wants to default to your normal boot drive (usually windows). 

[SIZE=4]RATS!!![/SIZE]

Everything went great on the separate drive install ----- except that. ](*,)

I'm sure I saw some utility that will allow me to GRUB the 2nd, (100% Ubuntu), drive, and restore the Windoze 7 drive to be self sufficient as before.  I am totally OK with the F11 start routine, because it comes up fast; it's just part of turning on the computer.

Thanks for all the help.  When you guys with the hard won experience share it's a ghood thing for us newbs.

Bruce Hinton

---

### Post by oldfred on 2010-08-23
Find your Ubuntu partition and mount that and install to sdb, instructions are generic for sda.

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sd[COLOR=Red]a5[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/s[COLOR=Red]da[/COLOR]
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/[COLOR=Red]sda[/COLOR]

You can reinstall windows boot loader from windows repair cd with fixmbr or BootRec.exe /fixmbr depending on win version.

OR:
Restore basic windows boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

