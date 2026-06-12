---
title: "Raid not recognized during install"
date: 2005-07-17
forum: Installation &amp; Upgrades
---

### Post by joe897897 on 2005-07-17
The problem is quite simple : :neutral: 
I've 2 disks of 80GB each i want to join in a raid 0
I use a promise fasttrack 100 TX2
I created the array with the raid utility: it gives me a 160GB array -> OK
During the ubuntu install, my disks are recognized as 2 separated disks of 80GB. :| 

Tried to format if under windows, gone OK but not better during ubuntu install ](*,) 
Tried to make a software RAID, red screen during install, impossibility to format/write to the new software raid. ](*,) 

Do i have to pass something on the command line before install or to make a disk with modules in order to make my promise raid card recognized ?

Many tanks for your precious help. :grin:

---

### Post by rotten777 on 2005-08-01
[QUOTE=joe897897]The problem is quite simple : :neutral: 
I've 2 disks of 80GB each i want to join in a raid 0
I use a promise fasttrack 100 TX2
I created the array with the raid utility: it gives me a 160GB array -> OK
During the ubuntu install, my disks are recognized as 2 separated disks of 80GB. :| 

Tried to format if under windows, gone OK but not better during ubuntu install ](*,) 
Tried to make a software RAID, red screen during install, impossibility to format/write to the new software raid. ](*,) 

Do i have to pass something on the command line before install or to make a disk with modules in order to make my promise raid card recognized ?

Many tanks for your precious help. :grin:[/QUOTE]


in the install, delete the partitions on the drives you're going to use. add a logical partition, choose the raid volume when it asks what type (instead of ext3)
then choose configure software raid. you should be able to pick it up after that ;)

---

### Post by schmappel on 2005-12-09
[QUOTE=rotten777]in the install, delete the partitions on the drives you're going to use. add a logical partition, choose the raid volume when it asks what type (instead of ext3)
then choose configure software raid. you should be able to pick it up after that ;)[/QUOTE]

That would probably kill my existing XP install, wouldn't it?

---

### Post by wae2288 on 2005-12-11
I have had problems kind of like that but once I solved those problems and I started to install the base system I could not get it to install the boot loader onto the raid 0. I played with ubuntu for a while on a different hard drive I really like it! 

This is my setup: 
lanparty ut nf4 ultra-d with raid enabled in the bios
two 36.7 gig raptors in raid 0
xp on the first partition
ubuntu on the second

any help with getting the boot loader to install will be greatly appreciated 

ps: I used to have ubuntu on my sata 300 gb hdd and windows on the raid 0 ubuntu was on the 5th partition with the grub boot loader on the master boot record because I have some windows files backed up on the 300 giger for some reason with it set up in this way I could not access some of the files on my 300 gb hdd on top of that windows would stop responding all the time for no reason that I could see and had to reinstall windows multiple times because it would freeze at the boot screen and couldn't get into safe mode or anything also after I deleted the ubuntu partition my xp problems were solved  but I must have ubuntu

---

### Post by wae2288 on 2005-12-16
I found that the problem was with my hard drive I ran chkdsk and it fixed all of my problems

---

