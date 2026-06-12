---
title: "Linux partitioner question pertaining to winXP"
date: 2005-06-30
forum: Installation &amp; Upgrades
---

### Post by Omnios on 2005-06-30
I have a good dual boot Linux install on a second 40 gig hard drive and and a main 120G hard driver which is ntfc. What I want to know will the Linux partitioner format a fet 32 section of the 120 gig hard drive and will windows still be able to read it. 

 I want to make a 40 gig partition to use for my Documents and in linux with the ability to share music and documents.
 
 I tryed doing it in Xp but the only way seems to be a reformat wich would loose a lot of my information which would take weeks of downloading to replace.

 Any help would be apreciated.

---

### Post by irusun on 2005-07-01
Yes, you can do it.  I can't list the detailed instructions (maybe someone else can), but maybe I can point you in the right direction.

You'll need to repartition your 120GB drive.

Use a partitioning utility such as gparted or partman to shrink the NTFS partition.

Use cfdisk (or maybe even the partitioning utility) to create a new FAT32 partition in the empty space.

Format it as a FAT32 filesystem using Linux or Windows.

Add it to your fstab file so that it's always accessible in Linux.

Do a forum search, there's lots of similar threads.  Hope that gets you started.

---

### Post by Omnios on 2005-07-01
Um little problem I played around with it today and could not make a new partition with partdisk in XP. Also just tryed to resize the 120g drive with gparted and also gtparted but that did not show up as an option. Think it has to do with mounting but not shure. Is there any other program I can use to resize? I mounted as in  unofficial Ubuntu starts guide which aperenty is read only.

---

### Post by michael_salcher on 2005-07-01
you could try it in windows by using 'partition magic'. but that costs money.

'qtparted' should be able to resize your ntfs partition. check [http://qtparted.sourceforge.net/features.en.html](http://qtparted.sourceforge.net/features.en.html) for what it can do. it seems like it can't create fat32 partitions. but if you can resize your ntfs partition, you can create a fat32 partition on the command line in linux.

---

### Post by Omnios on 2005-07-01
K figured it out you need ftfs tools from the ntfs project available in synaptic. Aperently Gparted can resise now but not shure if it does it without loosing data though. Any suggestions I kind of trust Gparted more but will go with whats best. I did a lot of reading and sometimes xp partition tables get screwed up making parts of the hard drive unreadable for xp.

---

### Post by mingus on 2005-07-01
[QUOTE=Omnios]K figured it out you need ftfs tools from the ntfs project available in synaptic. Aperently Gparted can resise now but not shure if it does it without loosing data though. Any suggestions I kind of trust Gparted more but will go with whats best. I did a lot of reading and sometimes xp partition tables get screwed up making parts of the hard drive unreadable for xp.[/QUOTE]

GParted, QTParted, Partman and Parted are all the same under the hood - libparted.  However, there are diff versions of libparted, and there have been bugs at times.

You are right to be very cautious about downsizing the NTFS volume with a non-native OS tool.  Before you attempt this, be sure you have a good backup.  Then in W$ run chkdsk /r (this may take quite a while), which will fix any broken chains and quarantine any bad sectors.  Then run the degragmenter.  This will compact all of your NTFS data to the front of the partition, which means less for Parted to move, and sometimes determines whether Parted will work or even try.  The sector check is important because it is not Parted's job to move data out of bad sectors to usable clusters, and again, this could cause Parted to fail (or for that matter, any partitioner). 

Try not to use different tools on the same partition.  DOS fdisk will not work for this, and Disk Manager should never be used along with another tool on the same partition.  If you do this from Linux, and the partitioner is working from free space, then either Parted or cfdisk should be fine but don't mix them.  And both of these are better than using fdisk, which calculates geometries a bit differently.

IMO, if you can get a copy of PartitionMagic, that is a better option for this job.

---

### Post by Omnios on 2005-07-01
Umm im kind of unlear on this I was thingking of using Gparted or Qtparted to resize the partition to about 60G and using disk manager to add a new partition for the free space and then formating in win to get fet 32 kind of figuring that this would lessen any problems with it as Linux ometimes has a hard time with ntfs. Got everything ready and am just going to transfer my essensial info to linux. What would you recoment for adding the second partion and formating to fat 32?

 The resise should go well the left over space is all free space.

---

### Post by mingus on 2005-07-01
*I was thingking of using Gparted or Qtparted to resize the partition to about 60G and using disk manager to add a new partition for the free space and then formating in win to get fet 32*

*The resise should go well the left over space is all free space.*

This probably will work if the disk is clean because it is simple.  But it adds to the importance of running chkdsk /r and then defragging - even though you see free space, there could still be a problem.  You absolutely want to avoid anything that may hang GParted, which could corrupt the NTFS record in the partition table.  I would create the single FAT32 partition with Disk Manager, because Linux is much better at reading from what W$ has done than the other way around.

Be sure to do that backup first.

Good luck.

---

### Post by Omnios on 2005-07-01
Well the good news ot the bad news!

 Gparted couldn't do it! Good is QTparted like a charm all the partition tables are good. Now I have a 60G XP drive (im not big on collecting software) and a 54G Documents drive for music recorded Tv programs I use my tv card as a dvr (works like a charm). Used the diskmanagement to make a new drive out of the partition. This all whent well.

 Now the bad part and this is kind of funny. Win XP will not format a fat 32 drive if it is bigger than 32G. checked the site and they recomend using win 98 or me disk to format it as fat 32. Problem I can not seem to do that with my very old first generation win 98 CD. Was thinking of fdisk but this was mentioned as a no no. 

 Any suggestions? My only reason to partition my main drive was to have a sort of my documents that could be shared with XP and Linux so having both read it is very important. Also comes in handy when doing reformats lol. 

 Anyways thanks for the great advise so far!

---

### Post by az on 2005-07-01
You could have just done everything with the Ubuntu installer.  Use guided partitioning to make your partitions on your other HD, then, shrink you ntfs partition, make a fat32 filesystem on the free space and give it an label entry in fstab.  

Offhand, I cannot remember the size limit fot fa32.  I think it is 32 megs, so you may have to split that partition again and make two smaller data partitoins.  Again, you can do this in two minutes while you install ubutntu.  Juse use the Hoary installer partitoner,

[https://wiki.ubuntu.com/forum/](https://wiki.ubuntu.com/forum/)

---

### Post by Omnios on 2005-07-01
Um thats the thing there are things including the win 98 and win me disks that will format a fet 32 over and xp can mount it. What I need to know is what I can use to make the format I have a 54G basic partition waiting for reformating. It is partitioned as an actual drive letter. 

 Problem is im not confortable running win 98 install to rormat this disk. I realy dont trust os installs all that much. I kind of tryed to check it with the win 98 install disk and got up to where it asked me if I wanted to write changes or not as it detected a nt (XP) setup. Also heard that Qtparted isnt all that good at formating fat 32.

 Does anyone know what I should use to fat 32 format a 54G blank partition what will garentie that It will be both readable and writable by both XP and Ubuntu? I would just do it but after doing a couple days of reading learn't there there are a lot of problems so looking for a working proven solution. 

 Thanks for all the help if this was XP id be borked. "Basicly reinstall and reformat or buy Partition magic lol"

---

### Post by Omnios on 2005-07-02
Actual thought I may add im trying to stick to native dos and or more XP fat 32 as possible not shure if QTpartied will work for that from what I read it is either Gparted or Qtparted that had problems formating in fat 32. As set up now the new drive partition Drive G is a simple blank raw partition.

 If it doesnt make a difference then I may go with a Linux fat 32 layout but prefer to keep it windows "Hack hack" to make shure windows may read and write it.

 Aperently you may use a X98 or ME start up disks format utility to do it but I only have a dusty Boot disk.

EDIT:
        problem solved used terminal with "  sudo mkfs.vfat -F 32 /dev/hda2  " command which makes a fat -F 32 makes it fat 32 and /dev/hda2 is the partioned hard drive which I used Gparted to make shure of the address. Checked and it all works in Xp and Linux.

 "'EDIT'": DO not forget to run chkdsk /r in windows terminal and defrage in XP!
This will solve any potencial partitioning formating problems.

In a nutshell
                     1: resized ntfs main partition with QTparted (Gparted did not work!).
                     2: used XP's Disk Manager to create a Primary unformatted partition.
                     3: formated with mkfs.vfat.     

 I would like to thank everyone for the help as it steared me away from big trouble lol. Thanks Guys!

---

