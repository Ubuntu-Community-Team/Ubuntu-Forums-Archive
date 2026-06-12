---
title: "Partitioning?"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by Yezinki on 2010-11-06
How to start from scratch step wise, partitioning a 300 GB HDD for Kubuntu only.

Number, types, sizes, etc of partitions?

Thanks.

---

### Post by oldfred on 2010-11-06
Need more info. Partitioning is unique to each user as to how they use system. Are you ging to add another root for experimenting or installing the next version. (I like to keep 3 root in rotation, so I always have old, current & beta installed). But if you plan to upgrade in place you do not need extra roots. Do you have lots of data?

Herman on advantages/disadvanges of separate system partitions
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

My standard recommendation:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up. Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough) but then you need swap equal to RAM.

Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)

---

### Post by Rubi1200 on 2010-11-06
+1 to everything mentioned by oldfred above.

The only thing I want to add is this:
I find it very helpful to sit down with a pen and paper and mark out how I want the partitions to look. That way, you can play around with different setups (partition size, which OS will go where etc.) BEFORE actually partitioning and, thus, avoid having to redo something because you may have miscalculated something.

---

### Post by ryadav on 2010-11-06
I use the following partition layout on my 1 TB =1000 GB drive

/boot   - partition size 150 MB
swap  - partition usually 2x your memory, i have 4G and use 6G for swap
/          - root partition minimum about 30 GB will work, I would give it 80 GB
/home - whatever you want, to up to entire disk

NOTE: swap size calculation used is: 2xRAM upto 2G, then 1G for each G of ram. so 4G RAM = 6G swap

i like to put my home on a separate partition, in case the system gets messed up. also i can reinstall / upgrade without worrying my /home partition and all my stuff will not get corrupted or deleted. a safer move would be to put /home partition on another drive, but you now got something to go

i don't worry to much about putting /var, /opt, /log, /tmp on their own partition, but if you like you can, google around for ideas

---

### Post by Yezinki on 2010-11-06
Thanks for your expert views:

HDD size = 298 GB seen in windows.

1.  30 GB NTFS for XP.

2.  10-80 GB Mount Point/Primary beginning ext4, is this the same as ROOT...is this where all Linux distros/Ubuntu variants are installed?

3. At least 2 GB Mount Point/Home....what is stored & shared in home?

4. 4 GB swap/logical..........shared by Linux distros if any besides Kubuntu?

5. Rest all NTFS Data/Shared for both Kubuntu & XP.

Install XP first.

Defrag, CHKDSK & partition  C using DD CD &  create NTFS Data/Share??

Install Kubuntu manually create Root/Swap/Home??

Kindly correct me.

Regards!

---

### Post by ryadav on 2010-11-06
See my reply inline

> **Yezinki said:**
> Thanks for your expert views:

HDD size = 298 GB seen in windows.

1.  30 GB NTFS for XP.

RY >> give it more space for you personal data, what do you plan on using more XP or Linux
RY >> give XP 150 GB and use the rest for Linux and it's partitions
RY >> create /home partition last give it all the remaining space!
RY >> your /boot and swap space are fixed, the other can vary in size
RY >> go with what I recommend below

2.  10-80 GB Mount Point/Primary beginning ext4, is this the same as ROOT...is this where all Linux distros/Ubuntu variants are installed?

RY >> I would recommend 20GB min for ROOT mounted on '/' (it's plenty)
RY >> yes this is were all the OS files and other particular stuff gets installed.

3. At least 2 GB Mount Point/Home....what is stored & shared in home?

RY >> no you want to have a lot of space for your personal files, data, etc
RY >> /home is were user account are created, all users files saved under /home/<user>

4. 4 GB swap/logical..........shared by Linux distros if any besides Kubuntu?

RY >> yes the swap partition can be shared, but not at the same time =P

5. Rest all NTFS Data/Shared for both Kubuntu & XP.

Install XP first.
Defrag, CHKDSK & partition  C using DD CD &  create NTFS Data/Share??

RY>> partition disk
RY >> sounds right, use MyDefrag utility to consolidate space
RY >> [http://www.mydefrag.com/](http://www.mydefrag.com/)

Install Kubuntu manually create Root/Swap/Home??

RY >> i would create a /boot partition, give it 150 MB
RY >> you are talking about creating partition
RY >> yes manually from the installer
RY >> you want a /boot partition just in case a kernel update corrupts something
RY >> partition are like firewall, damage is contained to that partition

Kindly correct me.

Regards!

RY >> Don't sweat-it the more you do it, the better you will get at it =) you can always start over again!

---

### Post by Yezinki on 2010-11-07
Thanks for your detailed reply.

Queries about a Linux only install:

Install Live CD delete, create partitions using the commands:

a. What about the /boot 150 MB & it's significance, when & where should it be created & file system?

 b. /home for a single Linux distro & /Data for multiple..but preferably on another partition.......strange  .........if Linux can share Data with windows why cant 2 Linux?

c. How many primary & extended> logical partitions on 1 HDD for a single Linux distro?

d.Install should be in /root.........size 20-80 GB according to HDD size?
/swap  size according to the RAM & all  left /home
          
e. Linux distro needs 4 partitions:
                             /boot, /root./ swap/ home or Data.............which should be mounted  their approx sizes & in which order should they be created?

f. What's this 2 GB /home mount point its significance?

Regards!

---

### Post by oldfred on 2010-11-07
Herman on advantages/disadvantages of separate system partitions
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

Herman makes good points on system partitions. If creating /home as a separate partition it needs to be larger than 2GB. /home normally has all your user setting often in hidden files & folders, but it also stores all your data unless you intentionally save it elsewhere or create other partitions & set those up to look like the standard locations where data is saved.  

I have both a /shared NTFS partition and a /data partiton. The /shared was for the data I wanted in XP & Ubuntu when I used XP a lot. But as my XP use declined I just created a /data partition and share most data with my Ubuntu installs. My firefox & thunderbird profiles are still in /shared. I did that originally as I was trying to learn Ubuntu & then my wife wanted to check email or internet & I had to reboot all the time (we share one computer).

---

