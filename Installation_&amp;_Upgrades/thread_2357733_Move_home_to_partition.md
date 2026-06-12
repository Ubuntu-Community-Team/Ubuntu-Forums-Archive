---
title: "Move /home to partition"
date: 2017-04-05
forum: Installation &amp; Upgrades
---

### Post by jerrylaz on 2017-04-05
I bought a new laptop from Dell with Ubuntu 16.04 LTS installed in a single partition.  I want to boot via cd and use gparted to shrink the partition.  I want to wind up a boot partition, a system partition, a swap partition, and a /home partition.

I want to do things the simple way and would appreciate a cookbook step by step.  One of my main questions is how to move /home to the new home partition so the system will recognize where it is.

I know I can wipe everything out and do a complete reinstall but that is not the way to go.  Besides, Dell may havbe a special version of Ubuntu with special drivers.  I do not know.  My laptop is being delivered mid April.

---

### Post by TheFu on 2017-04-05
You will get a /efi/, /, and swap at a minimum.  The other things /usr/, /var/ aren't necessary, IMHO. In the days of 1G of storage, having those things on separate storage made complete sense - /var would be local and /usr would often be over NFS. Just isn't necessary these days.  A case might be made for /var/ on a separate partition, but not if you have 20G+ storage.  Complex partitioning is likely to lead to wasted storage in a partition that doesn't need it.

Moving /home to a new partition isn't hard. Use the **usermod** command. There are options to move a HOME. It would be easier if you just mounted the storage for HOME somewhere else leaving /home/ empty on the older partition. The **usermod** manpage has all the details.  Think you want the -d and -m options. Maybe a few others. [https://linux.die.net/man/8/usermod](https://linux.die.net/man/8/usermod) - but be certain to check the manpage for your specific system. Sometimes options change. In ubuntu, usermod will move all the files and modify the passwd db for you.  Very simple.  No need to do it the hard way anymore (I've learned this in the last 3 months).

Current generation computers will come with uefi and GPT partitioning. GPT partitioning is a vast improvement over the old MBR/MS-Dos partitioning methods. No more "extended partitions" or "logical partitioning" due to limitations.  GPT allows hundreds of primary partitions - no hassles. Also, GPT has 2 copies of the partition table at opposite ends of the drive instead of next to each other. This protects against failures in nearby sectors.

The move-home-directory question is asked here a bunch. Do a little searching for steps about mounting the partition to a new directory (mount points are usually just an empty directory).  /u/ or /h/ would be common inside enterprises for HOME directories.  Using /home/ really isn't important, just convention. If the passwd db has the correct HOME, then all references to $HOME and ~userid and ~/ will work for anyone on the machine.

Dell would include the correct drivers. Some of those might be proprietary. Hopefully, they are dkim enabled.

---

### Post by oldfred on 2017-04-05
This has the step by step process to move /home.
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) 

I prefer to use /mnt/data for just folders in /home, but keep all of the mostly hidden user configuration settings in /home inside /. And I normally use about 25GB for / but only actually use less than half of it. I also do move some hidden folders with lots of data like Firefox & Thunderbird profiles. But my / is on SSD & data on HDD. And I have multiple installs, so that is why a /mnt/data may make more sense for me.

Dell develops sputnik which usually is later incorporated into Linux & then distributions. I did read somewhere that first sputnik for 12.04 was all in 14.04.


 Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en)
Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers)
Dell XPS 13 Developer Edition New Kaby Lake 16.04  Sputnik 
[http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml](http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml)
5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/)
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/)

---

### Post by SeijiSensei on 2017-04-05
I recommend making /boot a primary partition and allocating the rest of the drive to an extended partition.

---

### Post by oldfred on 2017-04-05
With UEFI and gpt partitioning there is only one type of partition or in effect all partitions are primary.
And with MBR you have the 4 primary partition limit or why if MBR you need extended partition. But with gpt you have a soft limit of 128 "primary" partitions. But if you want more there supposed is a way to change even that.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

