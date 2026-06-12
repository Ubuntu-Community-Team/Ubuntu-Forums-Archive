---
title: "Partitioning"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by Adrastus on 2010-11-06
Hey all,

Working the kinks out of a new install and trying to make sure I have everything just right before I go ahead.

So far:

[LIST=1]
[*]Win7
[*]/Data (NTFS)
[*]Ubuntu
[LIST=a]
[*]"/" 20GB (Cause I can --> 640GB HDD)
[*][COLOR=Red]**/Home**[/COLOR] ???
[*]Swap (I guess 6GB cause I have 6GB RAM)
[/LIST]
 
[/LIST]

So my first question is, how big should I make my /home partition if it's going to be separate from /data and only going to contain my settings etc.?  (I don't really know what goes in there besides some vague notions about settings to be honest.)

My second question is, after seeing this guide: [https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes) I'm wondering about the suggestion of a GRUB boot partition.   Is this dated?  Is this just the /boot partition the installer writes normally?  And are there advantages to making a separate /boot partition?  I'm still a fairly new user, but I expect to be doing some advanced stuff eventually, OS tinkering and home server kinds of stuff.

I can't wait to install!

--Adrastus

---

### Post by garvinrick4 on 2010-11-06
1. Windows 7 being now sda1 in linux and C: drive in Windows (primary partition)
2.extended partition big as you want to house logical partitions for / and /home and data. sda2 in linux: Make it big enough to hold all of them, bigger the better. (Will be a Primary partition) Just choose extended.
3. logical partiton for / big as you want if plenty of room lets 20 gig sda5 in linux ext4
4.logical partition for /home to hold all personals/picture s/docs/downloads/music and such 100 gig or so big as you want. sda6 in linux ext4
5 logical partition for /data big as you need will be sda7 in linux and a Letter such as G. or F. in Windows format as NTFS so can be used by Windows and Linux. ntfs
6. nothing for swap you got 6 gig that is more than enough Linux uses 500 meg at a full gallop. Just say no when it asks you warning no swap partition made. Swap is a scratch disk for extra RAM on HDD. 

Defrag windows 7 a couple of times to clean up. Put in Ubuntu CD and choose Try ubuntu
and open gparted and make your new partitions right in order from #2 to #5  Makes sda#'s on its own. And makes letter # in data / that will share with Windows. All NTFS partitions Windows can read.
Linux can read em all. EXT4, NTFS and FAT32.

---

### Post by Blackbird_13 on 2010-11-06
I've been using a separate boot partition for some time. I followed this guide initially.

[HTML]http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/[/HTML]Current advice I've seen seems to favour no separate boot partition, however, I'm sticky to my separate boot partition. I like experimenting and its dead easy with a separate boot partition to manually edit the grub.cfg file (contains entries for the operating systems you want to load, and how the boot menu looks). 

I suggest you create a small boot partition (mine is 100mb) and then install grub normally. You can try editing the grub settings via the separate grub config files and see whether you find it a pain (I did!).  You can then experiment with a separate boot partition at some later date.

Have fun.

---

### Post by Adrastus on 2010-11-08
[SIZE=2][FONT=Arial]Worked out great, thank you both!

Please see my post for my details if interested:
[/FONT][/SIZE][http://ubuntuforums.org/showthread.php?t=1590971](http://ubuntuforums.org/showthread.php?t=1590971)

--Adrastus

---

