---
title: "Need help partioning new system 2 drives"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by Xswitch on 2011-03-18
Hi all I need help setting up my new Laptop....

1st Drive = 90B SSD
2nd Drive = 500GB Sata
8GB = RAM

On my old system, I had one drive that was setup this way:

[B][COLOR="Blue"]/
/swap
/home[/COLOR][/B]

Here's what I'm thinking:

90GB drive will house all apps and system files, etc...
500GB would be for storage...  like a huge **/home**.  I looked at soem of the posts and I see people doing a **/virt** partition for their VM's.  I do use a VM, but do not really understand the **/virt** partition setup...  Definitely need help here.

Need some guidance on how to best set this up.  My plan is to clone the 90GB drive that will have ALL of my apps...  If the 1st drive fails, I can just pop in another drive and not miss a beat...

---

### Post by oldfred on 2011-03-18
With multiple drives I prefer to keep all of one system on each drive. For data that I have else where I mount it or mount  & link it.

I have not used vm's but do use a /data partition and link all my standard folders into /home from /data. I now do not have a separate /home, but keep it in / and it is only 1GB which is mostly my .wine which I have not yet moved to /data.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs (old, current, & beta) and rotate new versions from drive to drive. Then I can boot one or the other if either the install has issues or the drive had issues.

Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by Bucky Ball on 2011-03-18
90Gb is a lot of space for apps and system files ... 

I would probably stick /, /home and /swap on there as separate partitions then the 500Gb as data drive partitioned how you like; eg: /jukebox, /movies; whatever you need.

You could have a 100Gb /backup to clone the 90Gb drive to also.

---

### Post by carolinabranden on 2011-03-18
In Windows I have multiple partitions, but I put Linux all in one (to be changed) for test running Ubuntu 10.10 MM. A lot of your partition size plus order depend how you plan to use your computer. How are you planning to use your computer Xswitch? I've been researching about this on the internet to decide on my layout. The example below is from a combination of sources on the internet. (^_^) 

**_Partition_[COLOR="white"].....[/COLOR]_Mount_[COLOR="white"].....[/COLOR]_EFS_[COLOR="white"]....[/COLOR]_Size_**
/dev/_0[COLOR="White"]...[color="Black"]|[/color]...[/COLOR]/boot[COLOR="white"]........[/COLOR]ext4[COLOR="white"]....[/COLOR]1.7-2GB[COLOR="white"]...[/COLOR]SSD
/dev/_1[COLOR="white"]...[color="Black"]|[/color]...[/COLOR]/home[COLOR="white"].................[/COLOR]50GB
/dev/_2[COLOR="white"]...[color="Black"]|[/color]...[/COLOR]/usr[COLOR="white"].....................[/COLOR]19GB
/dev/_3[COLOR="white"]...[color="Black"]|[/color]...[/COLOR]/usr/local[COLOR="white"]...........[/COLOR]19GB
/dev/_4[COLOR="white"]...[color="Black"]|[/color]...[/COLOR]swap[COLOR="white"]..................[/COLOR]8GB[COLOR="white"]...........[/COLOR]HDD
/dev/_5[COLOR="white"]...[color="Black"]|[/color]...[/COLOR]/opt[COLOR="White"].....................[/COLOR]20GB
/dev/_6[COLOR="white"]...[color="Black"]|[/color]...[/COLOR]/var[COLOR="white"].....................[/COLOR]37GB
/dev/_7[COLOR="white"]...[color="Black"]|[/color]...[/COLOR]/tmp[COLOR="white"]....................[/COLOR]15GB
/dev/_?[COLOR="white"]...[color="Black"]|[/color]...[/COLOR]/ root[COLOR="white"]...................[/COLOR]7GB

Not the best list in the word. There are plenty of improvements that can be made to it. Anyone else want to add or change it?

[html]
**_Partition_[COLOR="white"].....[/COLOR]_Mount_[COLOR="white"].....[/COLOR]_EFS_[COLOR="white"]....[/COLOR]_Size_**
/dev/_0[COLOR="White"]...[color="Black"]|[/color]...[/COLOR]/boot[COLOR="white"]........[/COLOR]ext4[COLOR="white"]....[/COLOR]1.7-2GB[COLOR="white"]...[/COLOR]SSD
/dev/_1[COLOR="white"]...[color="Black"]|[/color]...[/COLOR]/home[COLOR="white"].................[/COLOR]50GB
/dev/_2[COLOR="white"]...[color="Black"]|[/color]...[/COLOR]/usr[COLOR="white"].....................[/COLOR]19GB
/dev/_3[COLOR="white"]...[color="Black"]|[/color]...[/COLOR]/usr/local[COLOR="white"]...........[/COLOR]19GB
/dev/_4[COLOR="white"]...[color="Black"]|[/color]...[/COLOR]swap[COLOR="white"]..................[/COLOR]8GB[COLOR="white"]...........[/COLOR]HDD
/dev/_5[COLOR="white"]...[color="Black"]|[/color]...[/COLOR]/opt[COLOR="White"].....................[/COLOR]20GB
/dev/_6[COLOR="white"]...[color="Black"]|[/color]...[/COLOR]/var[COLOR="white"].....................[/COLOR]37GB
/dev/_7[COLOR="white"]...[color="Black"]|[/color]...[/COLOR]/tmp[COLOR="white"]....................[/COLOR]15GB
/dev/_?[COLOR="white"]...[color="Black"]|[/color]...[/COLOR]/ root[COLOR="white"]...................[/COLOR]7GB
[/html]

---

### Post by oldfred on 2011-03-18
With desktops you do not need to separate system partitions. With a sever it may be better to isolate some partitions depending on what you are serving.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by carolinabranden on 2011-03-18
> **oldfred said:**
> With desktops you do not need to separate system partitions. With a sever it may be better to isolate some partitions depending on what you are serving.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Yep, it is optional. So long as it is done correctly it can be beneficial. Either way your computer should do fine as an average user. :D

---

### Post by Xswitch on 2011-03-18
Thanks everybody...  I'm just an average user carolinabranden.  Basically, I'm confused about creating a partition for my VM.  I'll be running Win 7 as a guest using Vbox.  Not sure if creating a separate partition is needed or warranted.  I don't even know how to do it.  lol...  I'm guessing that once the partition is created, then I would just install Vbox on the /virt partion????  Still fuzzy on the howto's and the pro's / cons...

SWEEEEEEEEET  ... That knock on my door is the UPS guy with my new laptop.... *"Oh yeah... Oh yeah...  It's my birthday...  It's my birthday..."*  LOL....  

Here are the specs:

[B]17.3" FHD (1920x1080) Super Clear Ultra Bright LED Glossy Screen
ASUS 30 Day Zero Bright Dot Guarantee
nVIDIA GeForce GTX 460M 192bit w/1.5GB GDDR5
Intel® Core™ i7-2630QM (2.0~2.9GHz, 45W) w/6M L3 Cache - 4 Cores - 8 Threads
ASUS Thermal Compound
[COLOR="Blue"]8GB (4 SODIMMS) DDR3/1333 Memory[/COLOR]
[COLOR="Blue"]OCZ Vertex 2 90GB SATA II Sandforce Solid-State Drive (275MB/s Sequential Write)
500GB SATA II 3GB/s 7,200 RPM Hard Drive[/COLOR] - Seagate XT NCQ Hybrid w/4GB SSD
Blu-Ray Reader/8x Super Multi Combo Dual Layer DVD +/-R/RW CD-R/RW Drive
Internal 8-in-1 Card Reader: MMC/SD/Mini-SD/XD/Memory Stick/MS Pro/MS Duo/MS Pro Duo
Built-in 802.11a/g/n WiFi Card
Built-in Bluetooth Wireless 2.0+EDR
Smart Li-ion Battery 8-Cell
Windows 7 Premium - 64-Bit Pre-installed w/Recovery Partition + Drivers & Utilities CD
ASUS Clean Windows 7 Install DVD - For a clean OS Install - No Bloatware or Scamware
Full Range Auto Switching AC Adapter
ASUS Gaming Mouse
ASUS Gaming Backpack
Global Two Year Warranty + 1 Year ADP + 24/7 ASUS Support [/B]

---

### Post by dabl on 2011-03-18
Your SSD will perform better if you align the partition(s) to the erase blocks/pages:

[http://www.linux-mag.com/id/8397/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%20%3A+LinuxMagazine+%28Linux+Magazine%3A+Top+Stories%29](http://www.linux-mag.com/id/8397/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%20%3A+LinuxMagazine+%28Linux+Magazine%3A+Top+Stories%29)

[http://www.ocztechnologyforum.com/forum/showthread.php?48309-Partition-alignment-importance-under-Windows-XP-(32-bit-and-64-bit)..why-it-helps-with-stuttering-and-increases-drive-working-life.&p=335049#post335049](http://www.ocztechnologyforum.com/forum/showthread.php?48309-Partition-alignment-importance-under-Windows-XP-(32-bit-and-64-bit)..why-it-helps-with-stuttering-and-increases-drive-working-life.&p=335049#post335049)

[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226&viewfull=1#post373226](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226&viewfull=1#post373226)

Beyond that consideration, your partitioning scheme is subject only to the same constraints as with hard drives (max. 4 primary partitions, need swap if you ever S2Disk, etc. etc.).

---

### Post by Hedgehog1 on 2011-03-18
> **Xswitch said:**
> Thanks everybody... I'm just an average user carolinabranden. Basically, I'm confused about creating a partition for my VM. I'll be running Win 7 as a guest using Vbox. Not sure if creating a separate partition is needed or warranted. 
 
The suggestion to make a completely seperate partition to store the Vbox files may be useful for someone who runs a lot of virtual machine(s) and needs a lot of disk space for them (or want seperation of file systems for them).
 
I don't think your few Vbox files will warrant that kind of seperation.
 
So, skip the** /virt** in your case.  The few you have will end up in your **/home**, and that is just fine.
 
***The Hedge***
 
:KS

---

### Post by Xswitch on 2011-03-18
Sweet... Thanks dabl...  thanks Hedgehog1... I'm divin' in...  LOL...

---

### Post by Hedgehog1 on 2011-03-18
> **Xswitch said:**
> Sweet... Thanks dabl...  thanks Hedgehog1... I'm divin' in...  LOL...

We are here if you need us!

***The Hedge***

:KS

---

### Post by Xswitch on 2011-03-22
Ok..  I still need some help...  LOL

90GB SDD (Here's what I'm thinking)  {**sda**}

[B]10GB       /

8GB        swap

72GB       /home ???[/B]


Second Drive is 500GB. {**sdb**}

Can I make the 500GB drive my **/home**?  If I do this, what should I do with the 72GB on the **1st drive**? 

Also, if I make the 500GB **/home**, will it automatically know that home is on sdb?  ***ie... the 2nd drive***?  Does it automatically link to that? 

How should the 500GB be set up, NTFS, ext4?

Thanks everybody...

---

### Post by oldfred on 2011-03-22
With 8GB of RAM you may never use swap. Only if you hibernate. But with an SSD you should be able to boot about as fast as a recovery from hibernation.

I would make / (root) about 20GB. Do you ever think you may want to try other systems? That may change recommendations.

I have 20 or 25GB for all my root including /home inside /. But I have all my data in other partitions and link in the data. With drives as large as they are now, I do not like to have one large partition, but several smaller. Filechecks can be run at different times, backups are somewhat easier, and if you have to recover from a partition error it is a lot quicker. The tradeoff is that if you fill one partition but have lots of space in another you then have to reorganize.

If you have some data you know you will use a lot, put that into a partition on the SSD. I would keep a 20GB system partition, perhaps the beta of the next Ubuntu or a copy of your last install on the 500GB drive, so it is always bootable on its own.

---

### Post by Xswitch on 2011-03-22
I see...  so you use the the /home inside of / to store data.  I see...  but what about these ?'s :

> Also, if I make the 500GB /home, will it automatically know that home is on sdb? ie... the 2nd drive? Does it automatically link to that?

How should the 500GB be set up, NTFS, ext4?

---

### Post by oldfred on 2011-03-22
My /home that is part of my root is only about 1GB and 750MB is .wine which I have not moved into my data partition (yet). All the rest of my data is in /data which is ext3 and /shared which is NTFS for sharing with my XP install which I use very little now. My / is about 6 or 7GB  with lots of programs installed so I have lots of room. You may need 4GB in /tmp when writing a DVD for backup.

Yes as long as the other drive is always mounted (not external) then it will mount it and use it. I do prefer to have all the system partitions (including /home) on one drive so I can always boot that drive. Then if the other drive fails I still can boot. Or each drive has a fully functional system. That may change when I decide to get a SSD but I do not think so.

If you are not sharing with any windows then your should use ext3 or ext4 for your partitions. If it is /home it has to be a Linux format as NTFS does not support ownership and permissions.

 Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

---

