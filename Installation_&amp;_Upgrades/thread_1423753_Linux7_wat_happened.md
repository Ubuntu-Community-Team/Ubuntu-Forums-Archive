---
title: "Linux/7 wat happened?"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by whitedemon on 2010-03-07
Can some one help me with this prob..

I earlier had windows 7 on a primary partition and installed xubuntu using "use large space available"

It worked and installed fine until i had my partition size manually expanded. That is i resized the partition size of the primary one to smaller size and simply played with it.

Unfortunately I found tat xubuntu is workin without any problems, but win 7 would not load, said some "bootmgr error, try to repair with windows cd."

Then with no other option left I had to reinstall the entire windows 7 and linux.. While partitioning (win 7) i gave 40g to win7 and 20g allocated to linux and 15g for t rest. But t last 2 partitions were "primary" durin the installation of win7. After installin 7, i tried to install linux, but it wud now not show the option "use largest available space". N i'm feared to go with the manual partitionin in linux as i'm a beginner in this. I also don't want to keep reinstallin windows again n again.

Kindly help

---

### Post by Phylax on 2010-03-07
First of all, have no fear. Actually partitioning manually during installation of ubuntu is a piece of cake as long as you know what a partition is and which file systems to use (I still recommend ext3 for Linux). Just make sure to set the mount point of the Linux System partition to "/", the installer won't let you proceed anyway unless you do so.

Unfortunately I doubt this will prevent the problem you have with Win7 not booting anymore. I only installed ubuntu on machine with Win7 once, and I had to repair the latter with the Windows CD. But this really wasn't any of a problem. The Win7 CD did the job. As far as I remember you just put it in as if you wanted to reinstall it and it will offer an "restore boot sectors" option of some kind...

consider this tutorial:
[http://lifehacker.com/251733/vista-tip--repair-bootmgr-is-missing-error](http://lifehacker.com/251733/vista-tip--repair-bootmgr-is-missing-error)

best regards from Bavaria

Phylax

---

### Post by Mark Phelps on 2010-03-07
> **whitedemon said:**
> ... It worked and installed fine until i had my partition size manually expanded. That is i resized the partition size of the primary one to smaller size and simply played with it.

Sounds like you messed with the Win7 partition size -- and did NOT use the Win7 Disk Management utility? Right?

If so, that is what corrupted your Win7 installation -- and will do that whenever you mess with it.

You will need a Win7 Installation DVD or Win7 Repair CD to fix the win7 problem.  Or, if you've already reinstalled and it's working again -- don't mess with the partition size unless you use the Win7 Disk Management utility to do so.

---

### Post by meierfra. on 2010-03-07
> said some "bootmgr error, try 
The "missing bootmbgr" error is usually cause by deleting the partition containing the boot files or  by  a misconfigured Grub, but not by resizing.  So  I think it's best to have a closer look at your setup: Follow these [instructions]("http://bootinfoscript.sourceforge.net") to run the boot info script and post the RESULTS.txt

---

### Post by kuvanito on 2010-03-07
i like to play a lot with computers and have learned the hard way with multi OS,if you want to have two OS on a puter (Ubuntu and 7) i recomend that you get two hard drives totally independent,if your puter has to bridges for IDE's use one bridge for each single hard drive,do not have both disc in the same bridge or better yet two SATA's disc each which it's own OS and for laptops,forget it,either it is Linux or Windows but I do not recomend partitions for multiboots and multi OS's.

---

### Post by yourelebowski on 2010-03-07
> **kuvanito said:**
> for laptops,forget it,either it is Linux or Windows but I do not recomend partitions for multiboots and multi OS's.

Don't be silly.  I've had no less than two operating systems on all of my computers for years, laptops included, using Windows and often multiple Linux variants. I've never had any troubles that were not easily fixable.  There's no reason to scare new users away from doing what is a most logical first step into Ubuntu.

---

### Post by whitedemon on 2010-03-08
Hey thanks to all those who have taken time to reply to my query.

I had no other option of reinstalling win 7 and in the storage management option, i made one partition to have it as unallocated space (Changed it from primary partition to unallocated and another from primary to logical)

Then restarted my system, and restarted again with the linux cd, it asked for "use large space uutilisation" and installed it successfully. 

Now i've got both OS working fine.. 

Thanks a lot for everyone. But I don't recommend this method, as I had just done it working by mere luck and 101 trials!!!!

---

