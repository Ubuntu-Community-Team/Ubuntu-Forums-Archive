---
title: "cfdisk error"
date: 2005-02-11
forum: Installation &amp; Upgrades
---

### Post by M-C A on 2005-02-11
Hi

I was trying to install linux on a partition on my laptop's harddisk. I got a copy of PartitionMagic and used it to split one of my partitions. Then I wanted to install knoppix via 'sudo knoppix-installer' on my harddrive and I used an other program (I think it is called something like 'qtparted') to make a linux swap and a ext2 partition.

I stopped the knoppix installation, because before I finished, I talked to some ppl using IRC and they convinced me, that knoppix is not the right thing for me.

After exiting the knoppix installer and rebooting the computer, I used PartitionMagic again to format the linux swap and the ext2 partitions back to FAT32.

I rebooted the computer again.

Then I wanted to change the drive letter's of my harddrives using PartitionMagic, but my first harddrive was not visible anymore as you can see [here](http://img58.exs.cx/img58/8716/partitionmagicerror16gb.jpg) 

I tried to use cfdisk in order to solve that problem, but cfdisk told me:

FATAL ERROR: Bad logical partition 5: Partition ends before sector 0

cfdisk is not showing me anything, just this error.

As the only option it tells me that it can delete the entirely partition table for that harddisk, but thet would destroy all my data on that harddisk. I cannot do this because WindowsXP is installed on that harddisk and I am not the only one who uses this laptop.

There must be a way to solve that problem.

By the way, Windows is working just as normal and is not recognizing that something is not right with the partitions of the harddrive. I can do everything, every program runs just as usual.

I think the error could be the following. During the use of qtparted under knoppix I deleted one FAT32 partition and first I created a swap partition. Then I wanted the whole rest of the partition to be formatted with ext2. There was about 8324,12 MB of free space, but after formatting with the ext2 filesystem there was still 0,5 MB free space, but I decided to not use this and closed the program. Maybe that little amount of free space is making the trouble?

Please help me! I don't know what to do :(

I can not install linux at the moment because of the cfdisk error, but I can not delete the whole harddisk or delete the partition table of the harddisk (which would be the same as deleting the whole hrddisk), because there are a lot of important files on an other partition of that harddisk, and an other operating system (windows). That is my dilemma!

---

### Post by ember on 2005-02-11
I remember having a similar issue with cfdisk, because of my Acronis True Image rescue partition - if I recall correctly, I used used parted instead of cfdisk. Maybe you'll try that.

---

### Post by M-C A on 2005-02-11
Do you mean parted instead of qtparted? I have used qtparted during the knoppix installation, and I suspect it to be the error's source.

---

