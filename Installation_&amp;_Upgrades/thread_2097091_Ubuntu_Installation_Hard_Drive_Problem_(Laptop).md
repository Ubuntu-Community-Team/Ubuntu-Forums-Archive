---
title: "Ubuntu Installation Hard Drive Problem (Laptop)"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by dkfilms13 on 2012-12-22
I downloaded Ubuntu 12.04.1 and put it on a USB drive (following the correct steps) and I am able to boot into Ubuntu when I boot from the USB drive. However, when I attempt to install the OS, it doesn't have any hard drives or their partitions show up as options for an install directory. 

**Hardware Specs: **
[LIST]
[*]Lenovo Ideapad u410
[*]Windows 7 x64 on a dedicated SSD
[*]500GB HDD
[/LIST]

I was hoping to partition the HDD and put Ubuntu on there so I could learn coding for ECE.

Will provide any additional details upon request. Thanks

---

### Post by sudodus on 2012-12-22
Welcome to the Ubuntu Forums :-)

It is good to know how your drives are partitioned before giving advice. When booted (a live session) from the Ubuntu install USB drive, please post the output of the following terminal window commands
```
sudo fdisk -lu
``` and ```
df
```You start a terminal window with the key combination
[I][B]
ctrl + alt + t[/B][/I]

Also, please make it easier for us and supply info about cpu, RAM, graphic chip and wifi chip. That will help if you need more help than about partitions. If not available in some of your documentation or via Windows, run the following GUI application, when booted (a live session) from the Ubuntu install USB drive:

***hardinfo***

or run the following command in a terminal window

```
sudo lshw>lshw.txt
``` and look for the data in the text file 'lshw.txt'.

---

### Post by dkfilms13 on 2012-12-24
Will do. In the meantime (if this post is even seen by anyone anymore) here are the specs (It's an Ideapad u410)-

500 GB HDD (For file storage)
32 GB SSD (W7 x64 OS)
8 GB DDR3 RAM
Core i5 third gen
Some cheap dedicated graphics card

I think the main problem here is the storage setup. I have 2 storage drives and between the two, Lenovo has partitioned them with the dumb partitions. 4 partitions (one for the OS on the SSD, the other big one for the file storage on the HDD) excluding a 200mb unformatted partition that can't be added to an existing partition w/o third party software.

---

### Post by oldfred on 2012-12-24
It looks like the Intel SRT.  Which seems to be the same from all Vendors.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)


Some examples that worked. Some installed to SSD, others to hard drive.
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it. 
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.
    

---

