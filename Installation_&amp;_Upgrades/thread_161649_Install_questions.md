---
title: "Install questions"
date: 2006-04-17
forum: Installation &amp; Upgrades
---

### Post by link141 on 2006-04-17
This is more of a question than a problem.  I have an 80GB hard drive in my machine and a 10GB hard drive in my machine as well.  I currently have Kubuntu installed on the 10GB hard drive, due to uncertainty about some of the partition methods.  Is there an idiot level way to easily split the 80GB hard drive in two equal partitions, one for Kubuntu and one for my existing windows OS, without messing up the hard drive?  If so, is there a way I can wipe the 10GB hard drive and make it available as write space for both OSs, without making my system unstable?  Although I know a good bit about computers, I have little idea how to run them :) If you need me to elaborate on what I mean, just ask.  Thanks to any one who helps :) .

---

### Post by cilynx on 2006-04-17
Look into gParted.  It's a nice graphical partitioner and you can get it on a LiveCD so that you can just boot to it.  With that, you can resize, move, delete, and create partitions.  It should be pretty straight forward to do what you want.  As for the 10GB drive, format it FAT32.  Both XP and Linux can easily read and write FAT32.

---

### Post by link141 on 2006-04-17
Thanks for the Advice!  I'll try that and look into it.  So with the 10GB drive, I'd be able to share data between though two systems?  Interesting that linux also uses FAT32.

---

### Post by mips on 2006-04-17
What is your Windows file system ?

You could use something like partition magic or one of the many free utils out there to repartition your 80G drive.

I would advise you create a addition /home partition for your data. this way if you ever have to reinstall your data is unaffected.

Once you have shrunk the windows partition the ubuntu installer/partitioner can work with the empty space left over.

---

### Post by mips on 2006-04-17
[QUOTE=link141]Thanks for the Advice!  I'll try that and look into it.  So with the 10GB drive, I'd be able to share data between though two systems?  Interesting that linux also uses FAT32.[/QUOTE]

Yes you will be able to share data once you have mounted the partion in ubuntu.
Keep in mind that the linux swap file has it's own partition and wont be part of the fat32 partition.

---

### Post by cilynx on 2006-04-17
Linux doesn't technically "use fat32", it just has a thorough understanding of it.  Natively, Linux goes on ext2, ext3, reiser, etc...

---

### Post by link141 on 2006-04-17
My windows partition is an NTFS.  So what you're saying is that I can put all of the linux system files on a small (maybe 2GB) partition, redirecting other files to another partition?  That releives some other concerns I had.  So say when Dapper becomes stable, that would allow me to reinstall Kubuntu without losing my Kubuntu data.  How can you define your home directory to another partition during install though, would it need to be a Kubuntu only partition, and is there a way I can do it from an already installed version?  I have Kubuntu installed on the 10GB drive.  As for the Utillities, can you give me a list of good formatting software?  Thanks.

---

### Post by link141 on 2006-04-17
Sorry that some of these questions were already answered, I wrote the preceding as you posted your response.

---

### Post by link141 on 2006-04-17
Sorry I have so many questions.  What is the linux swap file, and will it automatically mount the hard drive?  If not is there an easy way to go about this?

---

### Post by cilynx on 2006-04-17
OK, here goes:

What I Would Do (tm):

Using gParted LiveCD:
Cut the 80G drive 20/59/1.
Mark the 59G part for NTFS
Mark the 20G part for ext3
Mark the 1G part for Linux Swap
(If you're attempting to move mostly away from windows, maybe switch the ratios)
Make the entire 10G drive as one partition.  Mark it FAT32.

Using the WixXP Install CD:
Install Windows on the NTFS partition you marked earlier.
The installer should figure it out for you.  Just make sure you don't tell it to use the whole drive.

Using the Ubuntu Install CD:
"Manually Set Up Partition Table"
Install Ubuntu onto the ext3 partition you set up before.
When in brings up swap, point it to the Linux Swap partition from before.
Tell it to mount the 10G partition as /media/shared/
Proceed as normal.

Anything that you need to access in both OS's goes in /media/shared from the Ubuntu side and where ever Windows puts the drive on that side.

Some people like to put /home on a separate partition as well, but I don't recommend it for a normal desktop setup.  I always wind up running out of either /home or / with plenty of space left on the other.  If you don't split the partition, then they both share the same larger space.  

On a third note, if you ever do a server install, it's a good idea to do a lot of partition separation: /usr, /var, /home, /tmp, and sometimes /usr/local should all have their own partitions.  This prevents small-scale hardware failure from taking down the whole system.
You would get the same benefit on a desktop system, but you're more likely to buy a new hard drive before it fails.

Oh yeah: What is Swap?
Swap is a space on the hard drive that the operating system uses when there isn't enough RAM to go around.  It's much much slower than RAM, but it gets the job done in a pinch.  Windows uses random empty hard drive space for swap.  That's why it gets slower as you fill up the hard drive with data / games / mp3's whatever.  Linux designates a swap partition and thus the amount of data on your data partition has absolutely no impact on the speed of your system.

---

### Post by mips on 2006-04-17
[QUOTE=link141]My windows partition is an NTFS.  So what you're saying is that I can put all of the linux system files on a small (maybe 2GB) partition, redirecting other files to another partition?  That releives some other concerns I had.  So say when Dapper becomes stable, that would allow me to reinstall Kubuntu without losing my Kubuntu data.  How can you define your home directory to another partition during install though, would it need to be a Kubuntu only partition, and is there a way I can do it from an already installed version?  I have Kubuntu installed on the 10GB drive.  As for the Utillities, can you give me a list of good formatting software?  Thanks.[/QUOTE]

First you need to decide how much space you need for windows.

Then you can setup the (/) system partition, say 5GB. Then create a (/home) home partition, say 30GB. The setup the swap partition on the 10GB drive, say 1GB. This way your data and custom settings will reside in /home which is very nice should you ever do re-installs. The rest of the 10GB drive you can use as a backup for your most important files or something like that.

The partitions can be defined from the ubuntu installer/partitioner when you do the necesarry install. you have to highlight the one field and move the cursur bottons or something like that. Sorry cannot remember.

So you understood me right.

As for software just use the Gparted CD to resize your NTFS partion. The Ubuntu installer/partinioner will do the  rest of the partitioning and formatting.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by link141 on 2006-04-17
Thanks to both mips and cilynx.  You guys gave me some EXTREMELY useful information that saved me a lot of frustation.  This forum is awesome!

---

### Post by link141 on 2006-04-17
YIKES!!:mad: Two thirds of my hard drive is fried!!  That must be the reason that the ubuntu installer couldn't resize the partition in the first place.  I'm now glad that I backed up my data, because the hard drive is unstable!  Must be from my stupid syblings ricocheting about the house :mad:.  :-k But on the other hand...    this means my Dad needs to get me a new, and even larger hard drive :D.   Are there any known problems with any size of hard drive, brand, or type on linux?  Sorry if it feels like I'm creating new scenarios for just to annoy you with silly questions.  Thank you.

---

### Post by cilynx on 2006-04-17
I've never seen Linux care either way what kind of drive you use.  Personally, I like Seagate and stay away from Western Digital.  (Yes, I know WD used to be the best...too much bad luck recently.)  I'm currently running a pair of Seagate Baracudas, one EIDE, the other SATA.

---

