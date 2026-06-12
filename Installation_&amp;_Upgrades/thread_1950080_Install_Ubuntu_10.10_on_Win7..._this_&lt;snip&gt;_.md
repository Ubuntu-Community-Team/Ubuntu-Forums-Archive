---
title: "Install Ubuntu 10.10 on Win7... this &lt;snip&gt; wants 300GB of disk space!!!"
date: 2012-03-31
forum: Installation &amp; Upgrades
---

### Post by loucat on 2012-03-31
Hi guys!

I have a new laptop and I can't resist with windows 7 for more than 24 hours! I'd like to have win7 and ubuntu 10.10 with initial grub menu while booting, but I've never done it all alone and I'm having very absurd problems! :confused:

1) The worst one seems to be the reduction of win7 space, from its utility I'm not allow to give it less than 300 GB (out of 750)!!
Consider I've bought it yesterday and I've just install some updates, skype anf firefox :(
I've tried with its defrag, with Diskeeper, cleaning its disk space.. nothing!
I've heard about "shadows copies" but I'm not verysure of what they are and if/how I can delete them or disactivate them... 
I don't want to ruin anything!! (even if win7 will deserve to be ruined..)

2) I've downloaded and burnt the 64bit iso version (as I have an i5 processor), but actually Brasero gave me an error, it'd never worked in my old ubuntu. The disk seems fine anyway, do you think I should burn it again, maybe with K3b?

3) I'd like to create a data partition that is available both for win and ubuntu... I got that I have to use an NTFS partition, but do I have to do other things?
 
Thanks a lot, if you can remove giga from windows, I'll give them to you as (virtual) gift! :P

---

### Post by 2F4U on 2012-03-31
> 1) The worst one seems to be the reduction of win7 space, from its  utility I'm not allow to give it less than 300 GB (out of 750)!!
Consider I've bought it yesterday and I've just install some updates, skype anf firefox :sad:
I've tried with its defrag, with Diskeeper, cleaning its disk space.. nothing!
I've heard about "shadows copies" but I'm not verysure of what they are and if/how I can delete them or disactivate them... 
I don't want to ruin anything!! (even if win7 will deserve to be ruined..)

The disk fragmentation should give you a graphical layout of the distributions of files on the disk. Do you see anything towards the end of the Windows partition?

> 2) I've downloaded and burnt the 64bit iso version (as I have an i5  processor), but actually Brasero gave me an error, it'd never worked in  my old ubuntu. The disk seems fine anyway, do you think I should burn it  again, maybe with K3b?

If Brasero gives an error during the burn session, I would suspect that disk is not ok. You may get problems during installation. What was the exact error message? Some disk burners require that iso's are burnt at the lowest possible speed.

---

### Post by Bucky Ball on 2012-03-31
You are burning a disk image in Brasero? Maybe silly question but ...

---

### Post by loucat on 2012-03-31
> **2F4U said:**
> The disk fragmentation should give you a graphical layout of the distributions of files on the disk. Do you see anything towards the end of the Windows partition?


I see the big part at the beginning, and then a smaller part in the middle of the partition, quite far away from each other :(
Any clues?

And to reply both of you regarding the burning: I followed a guide and just right clicked on the file to burn it... and I suppose it chose automatically brasero as its default SW, but maybe I'll try again with another disk and with the other SW, using the lowest speed possibile.

thanks guys!

---

### Post by Bucky Ball on 2012-03-31
Open Brasero>Burn Disk Image>Select the Ubuntu ISO>Change speed to slowest.

Strange how you have had issues with Brasero. I have used it since I started using Ubuntu five years ago and has been faultless here ... ;)

---

### Post by ottosykora on 2012-04-01
>1) The worst one seems to be the reduction of win7 space, from its utility I'm not allow to give it less than 300 GB (out of 750)!!
Consider I've bought it yesterday and I've just install some updates, skype anf firefox <

in general, the windows partitioning unitily does not allow you to shrink a partition (even if empty) by more the 50%.
Why? No idea, ask MS.
But initially you need to do full defrag on that partition. Then shrink it to what ever windows allows you and then you have to run chkdsk on that partition first after rebooting etc.
Then defrag again and then try next shrink, it will allow you to shrink again, could be again 50% of what is here now. And so on.

For sheared partition, one can use ntsf today, but I still have one fat32 partition on my systems for that, it can solve sometimes problems with permissions as it does not use any , neither from windows nor from linux.

---

### Post by loucat on 2012-04-02
I burned the iso again with K3b and I didn't get any error, so I guess that thing is ok.

unfortunately even following Ottosykora's instructions for shrinking the volume (I shrinked it until half size, then scheduled a chkdsk at the first reboot), it doesn't allow me to shrink that partition anymore :(
now I have the O/S partition of around 350GB, another not allocated partition of 300GB (the freed space), plus a smaller partition for recovery data and another one which doesn't have any name (that was there from the beginning).

:(

any other "safe" ideas?
I'm afraid of trying with other SW besides windows tools 'cause I read that in windows 7 is risky :/

---

### Post by oldfred on 2012-04-02
This is for Vista but I think some of the same things apply. Also some have posted that other third party Windows tools may work also.

[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows]("https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows")

[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)
Resize Vista partition
If problems, try disabling system restore, pagefile, (in advanced settings in computer properties) and hibernate option (in power management). Don&#8217;t forget to turn them on back later.
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
shrink the primary partition from the Windows MMC.

Somone posted this:
You can also try downloading and installing the FREE version of Partition Wizard in Win7. It may allow you to safely shrink the Win7 OS partition more than does MS.

I had these links on dynamic partition issues which I think are the standard Windows tools.
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted with EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

---

### Post by Frogs Hair on 2012-04-02
If you get the partitioning sorted out you may want to consider a different release due 10.10 reaching end of life this month . [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by lJ9%3MR&gt;sa on 2012-04-02
Well, get a gparted cd iso and burn it. Boot to it and see if there is anyway to resize it, or if there are any other partitions. If you have an OEM partition, I recommend NOT removing it. Just resize that correct partitions. If it still won't resize or you were using gparted before, then I can no longer help you. BTW, I'm not a very big ubuntu/linux geek at all. :p

---

### Post by Mark Phelps on 2012-04-03
> **faxmanloveswaffles said:**
> Well, get a gparted cd iso and burn it. Boot to it and see if there is anyway to resize it, or if there are any other partitions. If you have an OEM partition, I recommend NOT removing it. Just resize that correct partitions. If it still won't resize or you were using gparted before, then I can no longer help you. BTW, I'm not a very big ubuntu/linux geek at all. :p

Do NOT use GParted to resize your Win7 partitions -- either the boot partition or the OS partition.  That's asking for trouble and is likely to leave you with a Win7 install that will not boot -- and no way to repair it.

---

### Post by loucat on 2012-04-09
thank you guys, I've finally found the time to try partition wizard and I think it did the job! Win7 now has now 80GB instead of 350, and still seems everything works :guitar:

now I'll try to create an extended partition from the ubuntu live cd... I'm not very keen on new things so I'll stick with the 10.10, but thanks for suggesting the latest release, sooner or later I'll take the courage!

THANKS!!

---

### Post by loucat on 2012-04-09
oh well now it seems everything OK excluding the 3rd point: the data partition!!
I've created a big data partition as a logical NTFS one, but windows doesn't see it :(
what should I do?

P.S. I've just noticed disk utilities says that my extended partition is misaligned by 1024 bytes and I should repartitioning :(
should I re-use partition wizard and try again? the os and everything is installed....

---

### Post by oldfred on 2012-04-09
The extended partition being misaligned is not critical because it is not a working partition but a container for all the logical partitions. As long as the logical partitions are aligned ok then it should be ok.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

### Post by loucat on 2012-04-10
Thank you very much, from one of the links you posted I got that the misalignment is not critical if it's related to the extended partition... not that I like to have the message "your partition is misaligned of 1020 bytes, this may result in very poor performance, repartitioning is suggested" :(
but if it's not a big deal I prefer not to touch anything! :)

and regarding the NTFS partition not visible from windows, it was a stupid setting of windows 7 which didn't show empty partition.

so thank you very much to all of you!

---

### Post by ledzepjes on 2012-04-10
I would second Mark Phelps, don't use gparted to manipulate your Microsoft Windows 7 partitions, it doesn't play nice with Microsoft partitions. You have a 50/50 chance of losing them, then you will need to use Testdisk and try to recover them if you can, very tedious.

also, @ 2F4U, Windows 7 doesn't show the defragmentation process graphically anymore, you have to use a 3rd party tool to do that. I recommend O&O defrag, free to use, install and defrag the hard drive, used it many times without fail. It has a particular setting that I find VERY useful, it can organize the contents of the partition to the front of the partition so all the free space is in the back, making it easier and more reliable when you need to shrink the drive. 

the feature is called "Optimize" free space
[http://www.oo-software.com/en/free](http://www.oo-software.com/en/free)

another good defrag tool is Auslogistics, also free, but I don't think it optimizes free space
[http://www.auslogics.com/en/software/disk-defrag/](http://www.auslogics.com/en/software/disk-defrag/)
(and you don't have to put in the email just to download, just go to cnet to download)
[http://cnet.co/zR4DB](http://cnet.co/zR4DB)

---

