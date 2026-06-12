---
title: "Ubuntu Fresh Installation"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by GeorgeOfTheBush on 2009-12-23
I have been working on Ubuntu 9.04 & 9.10 installed thru wubi, but have had a bad experience with frequent freezes and sh:grub> error.

As of now, I have Ubuntu installed on the same partition C:\ as Windows xp. 


[LIST=1]
[*]**Will the problem get resolved if I install Ubuntu on a separate partition?**
[*]I had used Easus Partition manager earlier which screwed up my windows installation, so I did not proceed with paritioning my hard disk. **Is there a better free partition manager with which I can create a Linux Partition?**
[*]**Lastly, How to install Ubuntu on the newly created partition? **My experience of Linux installation so far has been only through wubi.
[/LIST]

Any links, suggestions would be very helpful.

Thanks.

---

### Post by oldfred on 2009-12-23
While you can choose to just use the Ubuntu installer which gives you several default choices like entire disk or side by side installs where it auto shrinks your existing partition I prefer to do the manual install and create partitions in advance. But creating in advance requires some planning and understanding of partitions. You also have to have enough space to allow for the install after you shrink windows and windows wants at least 20% extra space to keep working well. With XP you can use gparted without problems if you have defragged your XP install and housecleaned it. May sure it boots after you create the new partitions but before you install. It probably will want to do a chkdsk.

You need at least 10GB for Ubuntu, probablly 2GB or more if your have lots of memory and want to hibernate for swap and more space for /home to store data and settings.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

I download the separate gparted liveCD, several other liveCDs that are repair type CDs. Create a USB bootable Cd as well as my new install CD. While I never have had trouble I like to have the insurance of other ways of booting system just in case. Of course you want to back up important data. I usually do not backup entire operating system as I would reinstall anyway but may save some config files that I know I edited. I then create partitions and use the manual install. I just did my portable that was always winXP and it took maybe an hour total. My desktop was more complex as I did a new install to a new drive and moved lots of data around to data partitions.

I also like to have a NTFS shared partition for photo, firefox and thunderbird profiles to make it easy for both systems to use the common files. You can read and write from Ubuntu into windows, but not read from Windows into the Ubuntu partition

---

### Post by GeorgeOfTheBush on 2009-12-23
My PC has just one partition C:\ drive of 80GB on which win xp is installed. Now I need to create partitions to install linux.

**Do I need to download GParted Live CD?** I just read in one of the links mentioned in the previous post that Ubuntu Live CD comes with GParted. If that's the case, **can I use the Ubuntu 9.10 Live USB that I already have to resize and create new partitions?**

This is what I intend to do using GParted.


[LIST=1]
[*]Resize windows partition from the current 80 GB to 60 GB.
[*]Create new **ext4** (or ext3?) partition of size 20 GB to install Ubuntu.
[/LIST]
Please give me ur suggestions. They would be very helpful to this newbie.

Thanks.

---

### Post by oldfred on 2009-12-23
How full is your windows partition? Windows really likes to have about 20% free to keep working.

You can use the gparted in Ubuntu, I just like using the gparted liveCD as it usually is slightly more up2date. You can use either ext3 or 4. Karmic now uses ext4 as the default.

You also need space for swap. Usually 2x memory if memory is less than 1GB. Equal to memory if memory is over 1MB.

---

### Post by GeorgeOfTheBush on 2009-12-23
Total hard disk space - 75 gb
Used by windows - 43 GB
**FREE Space - 32 GB**

I plan to give another 12 GB to windows, the remaining 20 GB to Linux. Is that ok?

So how much shd be reserved for swap? and what is it for?

---

### Post by audiomick on 2009-12-23
Hi.

Before you shrink your windows partition, clean up as much as you can, throw out old files, de-install anything you aren't using, and defrag, maybe a couple of times if it is an old install.

Shrink the partition using the windows tool, gparted live cd or ubuntu live cd. A number of people here suggest using windows tools for windows partitions with an OS in them.

Start windows a couple of times, and let it do any disc checking it wants to do. 

Then you can install Ubuntu into the empty space.

Swap is where the system writes to when the RAM gets full. If you want to use the hibernate function, it needs to be a bit bigger than your RAM, if not 1GB or so should be enough. If you let the installer work automagically, it will install a swap.

---

### Post by GeorgeOfTheBush on 2009-12-23
Michael.. 


[LIST=1]
[*]I did not understand the "**windows tool**" you mentioned for shrinking the partition?
[*]By **shrinking**, do you mean **resizing **the partition??
[/LIST]

---

### Post by oldfred on 2009-12-23
With Vista and win7 it is safer to use their partition editor to resize the partition. They changed the start from 63 to 256(?) that is not aligned the same.

With XP ,gparted is just fine as long as you have housecleaned and defragged your XP install.

---

