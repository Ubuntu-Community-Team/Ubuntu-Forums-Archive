---
title: "Making Win XP preinstalled laptop dual boot"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by psi36 on 2007-01-03
I've just bought a [HP NX7400 notebook]("http://www.backoffice.be/shop/details.asp?partid=RH399EA%23UUG"), with Windows XP Home Edition. 
It's arriving tomorrow or the day after tomorrow, but I guess Windows will be pre-installed on it. 
I want to make it a dual boot with Ubuntu 6.10 (32 or 64 bit, not sure yet).

My question:
How do I go about?

I guess I'll have to shrink the Windows partition before I install Ubuntu? How?

How much space do I have to keep for Windows? I'll be using it for Flash and maybe some small apps that don't run on Ubuntu. The laptop has a 80 gig harddisk, so not much room to spare.

I guess the best way to go about is make a third partition to share data between Windows and Ubuntu. What file system should I use for this? fat32?

How much room should I calculate for the Ubuntu partition? I'll be using OpenOffice, the GIMP, some VJ app and a bunch of basic stuff like Firefox, Amarok, ... and maybe even put an Apache test server with MySQL on there.

Windows will obviously be on the first partition, but should Ubuntu be on the second or should I put the shared partition as second?

---

### Post by hayz on 2007-01-03
Hello psi 36,
 I intend on doing the same thing on my pc[Hp Pavilion dv5215us]
 But, i was only able to learn frm the forum that i need to make a partition first.
But i dont seem to know how to go about that..](*,) 
Culd you help?:confused: 

You can check my thread out too -[Installing Ubuntu/Kubuntu]("http://ubuntuforums.org/showthread.php?t=328925")

---

### Post by jpyanowski on 2007-01-03
You may want to read this article for some info. Good luck. [http://www.ubuntuforums.org/showthread.php?t=328804](http://www.ubuntuforums.org/showthread.php?t=328804)

---

### Post by themusicwave on 2007-01-03
I setup my Dell Inspiron E1505 for a dual boot this summer.  It too came with windows preinstalled.

I chose to do a complete wipe of the windows install because it came with a lot of junk from Dell that was eating away windows resources.  This is probably the best option if you have a Windows re-install CD.  Sometimes the CD that comes with the laptop cannot install Windows if the hard drive is erased, so check this before erasing.   Always install Windows first. 

If you want to resize, Ubuntu will make it easy for you to resize the existing Windows partition.  If you simply want to shrink the partition, just let Ubuntu do it for you.  The installer has an option to shrink a partition, just tell it the size you want and let it go.  

Make sure you select a swap file size that is 2 times your ram.  So 1GB of ram gets a 2 GB swap.

Ubuntu will automatically install the GRUB boot loader for you so the dual boot will work without you needing to configure anything.  

For hardrive sizes, you could do a simple 50/50 split and give both OSe half the drive.  On my 100GB hardisk I made a 30GB NTFS partition for windows, 4GB swap, 30GB EXT3 partition for Ubuntu and 46GB FAT32 data partition.  Keep in mind that windows cannot see EXT3 partitions, and that Ubuntu cannot write to NTFS partitions(it's "experimental").   This is why I chose the data partition, to allow me to share files between the OSes. 

Also, a note on partitioning.  Some laptops come with strange little partitions, that are a few MB or so.  I would suggest not messing with them, I deleted them and some of my special media buttons no longer function.

Hope this is helpful.

---

### Post by bulldog on 2007-01-03
[http://ubuntuforums.org/showthread.php?t=282018&](http://ubuntuforums.org/showthread.php?t=282018&)

Read this and you know a lot more :D

---

### Post by hayz on 2007-01-03
@themusicwave: thanks for throwing more light on that for me..
> 
Sometimes the CD that comes with the laptop cannot install Windows if the hard drive is erased, so check this before erasing. Always install Windows first.

> Make sure you select a swap file size that is 2 times your ram. So 1GB of ram gets a 2 GB swap.
-Hoops! my pc's got a 1024MB ram that 2Gb Swap partirion?

> For hardrive sizes, you could do a simple 50/50 split and give both OSe half the drive
-Ok, I av got a 80Gb hard drive containing a Recovery Partition

> On my 100GB hardisk I made a 30GB NTFS partition for windows
-So the NTFS is for Windows, -see i didnt knw this b4.

> 30GB EXT3 partition for Ubuntu
-Didnt know dis neither.

> 46GB FAT32 data partition
-I wuld like a data partition too -to access my files frm both OS [So both OS can access a FAT32?]

> Also, a note on partitioning. Some laptops come with strange little partitions, that are a few MB or so. I would suggest not messing with them, I deleted them and some of my special media buttons no longer function.
-I wuld look out for that.

 Thanks Very much.
 -Did u take a look @ my thread i posted earlier for some shots i took recently in the Partition area of ubuntu? Pls take a look nd see hw u can guide me there.:D

---

### Post by psi36 on 2007-01-03
> **hayz said:**
> -I wuld like a data partition too -to access my files frm both OS [So both OS can access a FAT32?]
I have done that before and it works: both Windows and Linux can read and write FAT32.
But I think that if you want Windows to automaticaly recognize the shared data partition, it has to come right after the Windows partition. 
Can someone confirm this?

---

### Post by psi36 on 2007-01-03
I'm not planning on using Windows a lot, only for Flash development and maybe some other stuff I can't do on Linux. But since I've used only Linux for more then a year now, I don't think I'll be needing it often. Since my laptop comes with only a 80 Gig hard drive, I'd like to have as much space as possible for Linux. 
Is it possible to have XP Home on a 10 Gig partition? It'll only have Flash Professional 8 (which needs only 710 MB according to the sys req), Firefox and Internet Explorer (I make websites, so I need to test those on Win/IE).

Also: are there any drawbacks to using FAT32 compared to EXT3? I know it's an older, technically less good FS, but would there be any noticeable difference? 
I'm thinking of keeping my Windows data on my Windows NTFS partition and my Linux data on my Linux EXT3 partition and only use a small (like 10 gig) partition for shared data. This way I won't come into trouble if I install lots of apps on Ubuntu. 
Does this sound like a good or a stupid idea? 

If I only use 10 Gig for Windows and 10 as a shared FAT32 partition, I've got 60 Gig for Linux, which is of course way more then I'll ever need for applications. So the bottom line is: is there a good reason to put my (Linux) data on a EXT3 partition in stead on on a FAT32?

I'm studying Computer Science and FAT32/NTFS/Linux file systems are part of a course I have now, so I should (and do) know the difference from a technical point of view. But is this difference notable in daily use?

---

### Post by Bartender on 2007-01-03
Here's a [similar]("http://www.ubuntuforums.org/showthread.php?t=329474") thread - not because of the computer manufacturer (we're talking about Dells in that other thread) but because so many of the big PC assemblers are putting these goofy little "utility" partitions on the HDD's.  If you just had the single Windows OS partition it would be so much simpler.
Instead there are utility partitions and recovery partitions and "Media Direct" partitions (whatever the heck that is) etc. etc.  

The first few times you experiment with partitioning is hard enough without the extra distractions!

---

### Post by Afishionado on 2007-01-03
FWIW, I've had problems with repartitioning in the GUI installer...

First, boot Windows and make backup copies of all your files, just in case (!!!), then defragment the drive. Reboot with the Ubuntu CD, and use GParted to repartition before the actual install. Trying to resize partitions from in the installer occasionally causes it to lock up.

---

### Post by psi36 on 2007-01-04
> **Afishionado said:**
> First, boot Windows and make backup copies of all your files, just in case (!!!), then defragment the drive.
Since it's a new laptop, I don't have anything on it yet to backup and it shouldn't be fragmented. I do hope it comes with a decent recovery disk in case something goes wrong. I've heard that there isn't always one.

---

### Post by haiku99 on 2007-01-04
I recently bought an nx6310 and had no trouble setting up dual boot with Dapper or Edgy, partitioning worked fine and the install went smoothly.  Also, FWIW a really simple way to share data between the OS's is to use a USB flash drive, both read and write to mine no problem...this has been the case with a few different drives and with both Dapper and Edgy....

---

### Post by psi36 on 2007-01-04
> **haiku99 said:**
> I recently bought an nx6310 and had no trouble setting up dual boot with Dapper or Edgy, partitioning worked fine and the install went smoothly.  Also, FWIW a really simple way to share data between the OS's is to use a USB flash drive, both read and write to mine no problem...this has been the case with a few different drives and with both Dapper and Edgy....Hadn't thought of that. Sounds like a good idea!

---

### Post by gilbertr on 2007-01-04
The laptop you ordered is a T5500, so therefore you should use the i386 install CD.
As to possible configurations, have a look at the following [write-up]("http://www.psychocats.net/ubuntu/partitioning") - it helped me when I did the same on my T7200 laptop.

(BTW - is that the best price you could find for that (type of) machine ?)

---

### Post by psi36 on 2007-01-04
> **gilbertr said:**
> (BTW - is that the best price you could find for that (type of) machine ?)
That was actually quite a good deal. Notebooks are a lot more expensive here in Europe then they are in the US.

---

### Post by haiku99 on 2007-01-04
> **psi36 said:**
> Since it's a new laptop, I don't have anything on it yet to backup and it shouldn't be fragmented. I do hope it comes with a decent recovery disk in case something goes wrong. I've heard that there isn't always one.

My HP nx6310 did not come with a recovery disk, but had a menu option to burn the recovery partition data to CD's...11 of them, so this was a minor pain.  I did that and deleted the recovery partition to save 7GB on my small 40GB HD, have used the disks once to reinstall XP, this took forever but it worked OK...

---

### Post by bro on 2007-01-05
I must say that the Ubuntu partitioner hasn't always worked for my either. My experience with an HP-laptop is that HP has some kind of restore partition as part of their default windows install. Curiously enough this was a fat32 partition. 

I would take a bit more then the 10Gb for windows with Flash8. This program might need a lot of swap, which windows defaults in C:/ 
I'm running a dual boot myself and just backed up everything I wanted from windows, inserted the ubuntu cd, clicked install, gparted did work on my (no HP) laptop, 20 mins later, voila.

---

### Post by psi36 on 2007-01-05
Well, I tought 10 Gig might be a bit small. I'll probably go for 20 Gig for Win XP.
The rest will be for Ubuntu, I'm not gonna make a seperate partition to share data, I'll use an USB stick or external harddisk for that.

I might make two Ubuntu partitions though, one with a 32 bit version and one with a 64 bit version. I've learned from another thread I started in the "x86 64-bit Users" forum.
I'm not sure yet, because my diskspace is limited and it seems a bit stupid and difficult to have two versions of the same OS on one computer.
Maybe I'll just try the 64 bit version and see how stable it runs.

---

### Post by bro on 2007-01-05
> **psi36 said:**
> 
I'm not sure yet, because my diskspace is limited and it seems a bit stupid and difficult to have two versions of the same OS on one computer.
Maybe I'll just try the 64 bit version and see how stable it runs.

Well... you're saying it... :)

---

### Post by psi36 on 2007-01-05
> **bro said:**
> My experience with an HP-laptop is that HP has some kind of restore partition as part of their default windows install. Curiously enough this was a fat32 partition.
The partitions as they are now: shrunk the first partition to 20 GB (was 65 GB or so), so now there's 46 GB free space. 

And then there's a 9 GB fat32 partition (with lba flag), I guess that's the restore partition. 
Since I made two recovery point DVD's as HP calls them, I guess I don't need this? 
Can I just erase it to make my Linux partition bigger?

---

### Post by bro on 2007-01-05
I guess you can delete it. The HP I have this experience with was from a non-geek-friend so I just left it. She won't need the space. But it seemed a rather silly 'feature' to me. But I'm quite paranoied and make sure I have recovery/install cd's and backups of data in abundance anyway.

---

### Post by psi36 on 2007-01-06
I think I might keep the HP Win backup partition after all. 10 GB isn't that much and it might come in handy. I booted it and apparently it can store backups of My Documents and stuff like that. And there's also an option to backup Windows and then revert to the initial Recovery Point. So you can restore all your stuff from their. That and the fact that DVD's do degrade after time made me think it might not be such a bad idea to keep the backup partition.

I'll download the 64 bit version of Ubuntu on Monday (when my ISP download limit is reset) and install it then. I'm running the 32 bit version now and I'll be using them both for a while, untill I'm confident the 64 bit version is working. Is there a way to use the same swap partition for both Ubuntu's?

---

### Post by haiku99 on 2007-01-06
I'd definitely keep it if you don't need the space, I only deleted mine because my HD is 40GB....the backup CD disks I burned worked fine when I did a reinstall, but took a LONG time...

---

### Post by psi36 on 2007-01-08
I've installed the AMD64 version of Ubuntu 6.10, but now the 32 bit version isn't showing up in GRUB anymore. During partitioning I got an error because there where already 3 primary partitions. 

```
$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+   7  HPFS/NTFS
/dev/sda2   *        8588        9729     9170280    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            2551        4462    15358140   83  Linux
/dev/sda4            8339        8587     2000092+   5  Extended
/dev/sda5            8339        8587     2000061   82  Linux swap / Solaris

Partition table entries are not in disk order
```
Could it be I installed the 64 version over the 32 version?
How can I work around this (when I do a reinstall, i know I can't recover the partition if I installed over it)? Is there a way to have more then 3 bootable partitions on a disk?

Well, if I've installed over the 32 bit version, I don't think I'll be reinstalling it anyway. Not as long as I don't experience to big problems with the 64 bit version.

---

### Post by psi36 on 2007-01-12
Since I'm having some trouble to get everything running the way I want in the 64 bit version of Ubuntu, I'll be reinstalling the 32 bit version, but I want to keep using the 64 bit version as well.

I have 3 bootable partitions now: Windows XP, Ubuntu amd64 and the HP backup and recovery partition. Is it possible to add a fourth bootable partition? I got a message the last time that I had to make an extended partition, since I already have the maximum of primary partitions.

How should I go about to make sure I don't put the new Ubuntu over the old one, as I did last time?

---

