---
title: "Extended Partition Question during Installation"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by silvrdragona on 2006-12-08
This is my first time installing/dual booting Ubuntu, I am using the LiveCd 6.06.

I am having trouble creating the partitions for ubuntu. 

This was how I wanted to split the space of the drive, the total is about 140 gigs.  

Windows xp 65 Gigs (Left Alone)

Ubuntu 35 gigs
shared (fat32) 25 gigs
/home 10 gigs
swap 5 gigs

I was trying to create the various partitions for the seperate drives and gparted would not let me.  I think this might have to do with the extended partition being used with windows already. 

Here is a link to the screenshot.

[[IMG]http://img134.imageshack.us/img134/4941/screenshotob9.th.png[/IMG]](http://img134.imageshack.us/my.php?image=screenshotob9.png)

Should I just enlarge the extended partition to the full drive space and create logical partitions?  Can ubuntu be installed onto a logical partition?

Anyone have the solution to my problem?  

Thanks!

---

### Post by daniminas on 2006-12-08
This is what i have and work fine for me:

Ubuntu Drapper (primary)
Windows XP (primary)

/home (Extended)
/storage (Extended)
/swap (Extended)

You can't make more than 4 primary partition.

good luke;)

---

### Post by mechanic on 2006-12-16
> **silvrdragona said:**
> 
Should I just enlarge the extended partition to the full drive space and create logical partitions?  Can ubuntu be installed onto a logical partition?



This question doesn't seem to be answered in the available installation guides, and it's an important one. I spent some time trying to find information on this very point on here, no joy.

However, I can tell you from experience that yes, you can install to a logical partition. No doubt this is how you could set  up a system with several linux flavours available at boot time.

There are some issues with the current U. 6.10 install CD, not least the gparted and mount points problem in the install process. I found that running gparted before starting the process and setting up the root, home and swap partitions, then running the install application and just passing the 'set up your own partition scheme' without further changes worked smoothly. 

See here:
[http://ubuntuforums.org/showpost.php?p=1700787&postcount=29](http://ubuntuforums.org/showpost.php?p=1700787&postcount=29)
for a workround to the 'no root filesystem' error that can occur at this stage.

Regds, m.

---

### Post by moshuptrail on 2006-12-16
I like mechanic's approach.  In learning about and playing with Ubuntu I must have installed it on 4 different computers at least 10 different times, and I think the smoothest install is when I use the Gparted Live CD first, to define all the partitions and filesystems, and THEN run the Ubuntu install.

Windows installs itself in a primary partition that takes the whole drive.  Typically you shrink that to make room for Ubuntu.  If you need more than 4 partitions total, you must use an extended partition.  I've had good luck with one extended partition that has three logical partitions within it: one for /, one for swap, and one for /home.  That's a pretty simple layout.

So the entire Ubuntu install resides within the extended partition.  Once you've done that, you pretty much can forget about it.  I don't think there's any difference between a primary and a logical partition once you get going.

Oh yes, one gotcha:  If you just define partitions and forget to format them, the Ubuntu install may crash.  (Experience is a dear teacher, but fools will learn at no other, Mark Twain)

---

### Post by sincereheart on 2006-12-25
Merry Christmas to all the GEEKS.

I am new Linux. 
I am trying to install Ubuntu Server Edgy 6.10.  I am wanting to learn VSERVER - XEN.

Main Problem:
During the install I am unable to create an Extended Partition - so that I can further partition it into 2 or 3 partitions. 


Here is what I am trying to do:

200Mb for hda1 (/boot)
  2Gig for hda2 (swap)
  10 Gig for hda3 (/)
hda4 gets the rest as an extended partition
  split it into 10 Gig for hda5 (/usr)
  and 10 for hda6 (/var)
 the rest can goto hda7, 218Gig  (/vserver)

Here is what is happening:
I am able to create hda1, hda2, hda3 as Primary Partitions.
I am also able to create hda4 as "LOGICAL" Partition.

However I am not able to find any way to further split hda4.

(I even tried creating hda4 as Primary and then tried to split.... but unable to find a way to do that during installation).

Here are my questions:
1.  What are my options. 

2.  In this post some one suggested to create the partitions befor doing the install.
So how do I partition before hand. Where from may I download the gparted or any other suitable software. So once I do that then how do I install Ubuntu Server.

3.   After installation of Ubuntu I want to install XEN. This will contain Windows as well as Ubuntu VSERVERS. So what file system do I choose.  (So far I am going with Ext3). 

4.  My Ubuntu 6.10 (Edgy Eft) CD is about 2 weeks old download. If this was a known bug and has now been solved then would it help if I simply download the latest version and burn it on a new CD.

I will appreciate any help. Thanks.

---

### Post by sincereheart on 2006-12-25
Just as an FYI.
I am not using LIVE CD. Rather I am using the standard downloaded CD. Thanks.

---

### Post by bulldog on 2006-12-25
You make a small mistake :D 

Your fourth partition should be the extended partition,which covers all of the available free space.
In this extended partition you can create your logical partitions.

---

### Post by sincereheart on 2006-12-25
How do I create extended partition. 
During the process I have only two options to select from:

a.  PRIMARY  // I have already selected this for the first 3 partitions.
b.  LOGICAL //  I have tried to select this for the 4th partition. 

So out of these two options ......
So where can I find an option that says "EXTENDED PARTITION".  Even I tried making the fourth partition type as PRIMARY. Still I could not find a way to Make it Extended or to further split this...

---

### Post by bulldog on 2006-12-25
It's possible if you can only choose between this two,it create an extended partition for you by choosing logical.
You can't make a logical without an extended so it should be there.

If you have [example] 100GB free,make a logical of 10 GB and make another one of 20GB,if this can be done,you'll have an extended partition already.:D

---

### Post by sincereheart on 2006-12-25
Great. Seems like working. 

I am now trying to create hda7. This is meant for XEN - (Virtual Servers).


So what file system will be appropriate for this.
I will have a combination of Windows and Ubutu as Virtual Servers.

Will EXT3 work for this i.e. both Windows and Ubuntu.

... or do I have to go by FAT32 or NTFS...(I am sure these work for windows ... but not sure if these will work for Ubuntu.

---

### Post by bulldog on 2006-12-25
Windows should be NTFS and linux can be ext3.

If you wont them both read and write to the same partition you need FAT32.

---

