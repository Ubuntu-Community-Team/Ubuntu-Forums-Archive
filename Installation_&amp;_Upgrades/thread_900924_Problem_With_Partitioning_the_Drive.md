---
title: "Problem With Partitioning the Drive"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by caleb.gross on 2008-08-25
When try to install Ubuntu from the LiveCD and I come to the window where it gives me the different options for partitioning, I am missing the first (easiest) option, leaving me only three remaining options. I am relatively new to partitioning hard drives, but otherwise I am pretty computer savvy so this has just got me stumped. Does anyone know what I'm talking about? Any help would be terrific ;)

---

### Post by sandysandy on 2008-08-25
do u have windows also installed.

if yes, see these links on dual booting XP & Ubuntu

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)****

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

regards

---

### Post by manishtech on 2008-08-26
> **caleb.gross said:**
> When try to install Ubuntu from the LiveCD and I come to the window where it gives me the different options for partitioning, I am missing the first (easiest) option, leaving me only three remaining options. I am relatively new to partitioning hard drives, but otherwise I am pretty computer savvy so this has just got me stumped. Does anyone know what I'm talking about? Any help would be terrific ;)
I personally suggest people to use Manual Partition, though it might be tough for a newcomes, still the dangers are minimized.

People ask me that its tough since everything has to be done manually. This is the thing what we want, we know what we are doing. :)

---

### Post by caleb.gross on 2008-08-27
Thanks, you guys are awesome. Real quick though, I came across this..

Create a swap partition of at least your amount of RAM (if you don't know, 2000 MB is a good value). 

What does this mean?

---

### Post by stevemid on 2008-08-27
> **caleb.gross said:**
> When try to install Ubuntu from the LiveCD and I come to the window where it gives me the different options for partitioning, I am missing the first (easiest) option, leaving me only three remaining options. I am relatively new to partitioning hard drives, but otherwise I am pretty computer savvy so this has just got me stumped. Does anyone know what I'm talking about? Any help would be terrific ;)
I have the same problem in that the disk partitioner does not display the options which the instructions say it should display.  I am getting my instructions from [https://help.ubuntu.com/8.04/switching/dualboot-procedure.html](https://help.ubuntu.com/8.04/switching/dualboot-procedure.html) .  In step 5-6 where I select my windows partition and press enter, I am not presented with a size option, only an edit or delete option and neither of these lead to choices for size.

---

### Post by caleb.gross on 2008-08-28
Ok so I'm trying to manually partition the drive with the Ubuntu installer and my screen looks like this:

/dev/hda
  /dev/hda1   ntfs       120023 MB unknown
  free space             8 MB


Im having trouble understanding what to do here. I have XP already installed but its giving me the blue screen so I'm only able to use my laptop by means of the LiveCD at this point.

---

### Post by Bucky Ball on 2008-08-28
Use manual partitioner when installing, just avoid the partition (and leave) which is NTFS. That is where your windoze install is. I advise getting a piece of paper and pencil, a cup of tea (coffee, beer or scotch or whatever) and taking half an hour away from the computer to plan what you need and dividing up the available space on your hard drives. Then get to work!

Windoze in first (first partition), if it isn't already there, then reboot and install Ubuntu and hit 'manual partition'. Check your plan and partition away. As mentioned, twice the swap of your available ram (1gig of RAM = 2Gig swap partition) and the rest is up to you.

Base requirements for partitions:

/
/home
/swap (twice your ram size)

/ = root
/home = user info/data
/swap = swap

Format them all as EXT3. One thing to remember here, though, and this will be incorporated in your original plan: Windoze does not recognise EXT3 partitions at all for reading and writing. I usually set up a FAT32 (or vfat) partition for sharing data between the two operating systems. It will show up in both, no problem. 

Again,* leave the NTFS partition completely alone!*

Good luck. :) Oh, and welcome!

ps: Installing Ubuntu may rectify your blue screen problem (by setting the correct targets for your boot loader, in Ubuntu's case, Grub (although there are others)). Your Windoze blue screen may, of course, be disrelated to any of this and a problem with the Windoze install. Was Windoze booting okay before you started on this adventure?

pps: Stevemid, we are all good, honest Joes and Josephines here (!) but maybe not a good idea to use your email address as your handle ... :)

---

### Post by manishtech on 2008-08-28
> **caleb.gross said:**
> Ok so I'm trying to manually partition the drive with the Ubuntu installer and my screen looks like this:

/dev/hda
  /dev/hda1   ntfs       120023 MB unknown
  free space             8 MB


Im having trouble understanding what to do here. I have XP already installed but its giving me the blue screen so I'm only able to use my laptop by means of the LiveCD at this point.
Fine caleb!

I am assuming that you are giving 20 GB out of 120GB to Linux.

I can see that you have a primary partition called /dev/hda1 which has windows installed. Now boot from LiveCD. Goto System>Administration>GNOME Partition Editor (Gparted in short).

Now in Gparted, select hda1 and click on resize, try to create a new Extended partition of size 20GB.
Click on Apply, so that a new extended partition is created.

Now after extended partition is created, you need to create logical partitions in it. Select that extended partition and click "New". In that create a partition of size 19GB for installing ubuntu which should be of type Logical and filesystem ext3 or reiserfs. Create another partition of the rest space left which should be 1GB. This 1GB partition should be of type logical and filesystem linux-swap.

Now click on "Apply". So that these two partitions are created. Now after these two partitions are created, you can click on "Install" to install ubuntu. I first suggest you to to the partitioning and then return back to this forum. We should do slowly, as overdose of information and guidance can be dangerous :D

**Information**: Any hard disk can have three types of partitions - primary, extended and logical. 
Extended partition encapsules all the logical partitions. There can be only one extended partition in a hard disk which contains all the logical partitions inside it.
You can have only a total of 4 extended and primary partitions. Means 1 extended and 3 more logical are allowed or all 4 primary are allowed.

Windows needs a primary partition to install, this is not a problem for linux. Linux can be installed in any partition type.
Additionally, you cannot install anything inside an extended partition since its just a wrapper to hold logical ones.

---

### Post by manishtech on 2008-08-28
> **Bucky Ball said:**
> Use manual partitioner when installing, just avoid the partition (and leave) which is NTFS. That is where your windoze install is. I advise getting a piece of paper and pencil, a cup of tea (coffee, beer or scotch or whatever) and taking half an hour away from the computer to plan what you need and dividing up the available space on your hard drives. Then get to work!

Windoze in first (first partition), if it isn't already there, then reboot and install Ubuntu and hit 'manual partition'. Check your plan and partition away. As mentioned, twice the swap of your available ram (1gig of RAM = 2Gig swap partition) and the rest is up to you.

Base requirements for partitions:

/
/home
/swap (twice your ram size)

/ = root
/home = user info/data
/swap = swap

Format them all as EXT3. One thing to remember here, though, and this will be incorporated in your original plan: Windoze does not recognise EXT3 partitions at all for reading and writing. I usually set up a FAT32 (or vfat) partition for sharing data between the two operating systems. It will show up in both, no problem. 

Again,* leave the NTFS partition completely alone!*

Good luck. :) Oh, and welcome!

ps: Installing Ubuntu may rectify your blue screen problem (by setting the correct targets for your boot loader, in Ubuntu's case, Grub (although there are others)). Your Windoze blue screen may, of course, be disrelated to any of this and a problem with the Windoze install. Was Windoze booting okay before you started on this adventure?

pps: Stevemid, we are all good, honest Joes and Josephines here (!) but maybe not a good idea to use your email address as your handle ... :)
How can he install Ubuntu without touching the NTFS partition? It is the only partition on his system and it has to be resized. Correct me if am wrong!

---

### Post by Bucky Ball on 2008-08-28
One huge primary partition using the whole disk? Resize it is, then.

---

### Post by Sef on 2008-08-28
> Create a swap partition of at least your amount of RAM (if you don't know, 2000 MB is a good value). 

Swap doesn't need to be more than 1GB (1000MB.)  If you have 512 mb ram or less then 1.5 - 2 times ram is fine.   Above 512 mb ram, then 1 GB is the biggest swap that is needed.  With more than 2 GB ram, swap is not really needed.

---

### Post by manishtech on 2008-08-28
> **Sef said:**
> Swap doesn't need to be more than 1GB (1000MB.)  If you have 512 mb ram or less then 1.5 - 2 times ram is fine.   Above 512 mb ram, then 1 GB is the biggest swap that is needed.  With more than 2 GB ram, swap is not really needed.

If you have 1 GB of RAM then swap can be some 500MB.
I have 2GB RAM and 700MB swap which I had created long time back. The swap usage is always zero :) 

With 512MB of RAM I dont think you need more than 700-800MB of swap unless you want to try out many applications and compiz effects!

---

### Post by caleb.gross on 2008-08-28
So in creating a 20GB partition for ubuntu, does that mean that I'll only be able to access 20 GB of space while using ubuntu? Meaning that I'll only have that 20GB of space to store pictures, video, etc... or will I still be able to use the other 100GB for storage as well?

Oh and quick update: when I try to resize the primary partition (114463 MB) it tells me the minimum size is 114463 MB and the max is 114471 MB. The 8 MB difference is due to the 8 MB of unallocated space left in the drive. So apparently it's not wanting to let me resize it. 

/dev/hda1 also has an exclamation point next to it, I right clicked the partition and clicked "Information" which tells me:

Warning
ntfsresize v2.0.0 (libntfs 10:0:0)
Error reading $Mft record(s): Input/output error.

It repeats that last line about a hundred times.

---

### Post by manishtech on 2008-08-28
> So in creating a 20GB partition for ubuntu, does that mean that I'll only be able to access 20 GB of space while using ubuntu? Meaning that I'll only have that 20GB of space to store pictures, video, etc... or will I still be able to use the other 100GB for storage as well?Ubuntu (Linux in general) can read/write a vast number of filesystems. Your windows partition can be read and written too. Dont worry, the whole 120GB of hard disk is at your disposal when using Ubuntu and only 100GB when using Windows :lolflag:


> Oh and quick update: when I try to resize the primary partition (114463 MB) it tells me the minimum size is 114463 MB and the max is 114471 MB. The 8 MB difference is due to the 8 MB of unallocated space left in the drive. So apparently it's not wanting to let me resize it. 
Oh God! I think its due to fragmentation and pagefile.sys problems. You need to defragment it somehow to let it be resized.

> /dev/hda1 also has an exclamation point next to it, I right clicked the partition and clicked "Information" which tells me:

Warning
ntfsresize v2.0.0 (libntfs 10:0:0)
Error reading $Mft record(s): Input/output error.
I cant figure our about this error, looks like some filesystem issue. I should ask the experts. Till then try to do a file system check. Install ntfsprogs package using the command
```
sudo apt-get install ntfsprogs
```Then after this is installed, make the filesystem check using this command
```
sudo fsck.ntfs /dev/hda1
```It repeats that last line about a hundred times.

---

### Post by caleb.gross on 2008-08-28
Ok it tells me that ntfsprogs is already the newest version, and when I enter sudo fsck.ntfs /dev/hda1 it tells me sudo: fsck.ntfs: command not found

And I cant find a way to defrag the comp in ubuntu

---

### Post by caleb.gross on 2008-08-28
Ok Ive decided that I don't need Windows installed anymore, its unusable at this point anyways.. is there any reason why I would need to keep it? Could I reformat the computer and just run Ubuntu independently?

---

### Post by caleb.gross on 2008-08-28
Ha ok guys thanks for all the help. I ended up just dedicating the whole computer to Ubuntu. Peace

---

### Post by Bucky Ball on 2008-08-28
Nice; simple and easy. Good luck and don't forget to repost if you have anymore probs. Don't forget to have a think about what partitions you need and make a plan before you start. :)

[http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml)

---

### Post by manishtech on 2008-08-29
> **caleb.gross said:**
> Ha ok guys thanks for all the help. I ended up just dedicating the whole computer to Ubuntu. Peace
That solved the problem itself. Now your system is completely free, without any restrictions. 

No! Wait.. You are also free...

> And I cant find a way to defrag the comp in ubuntu
Well, you have to defrag the partitions in windows itself. I dont know any such tool in linux.

---

