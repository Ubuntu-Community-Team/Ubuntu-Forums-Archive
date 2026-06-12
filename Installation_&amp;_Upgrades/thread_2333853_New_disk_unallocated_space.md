---
title: "New disk unallocated space"
date: 2016-08-13
forum: Installation &amp; Upgrades
---

### Post by kiranshri on 2016-08-13
I am relatively new to Ubuntu and PC building in general.


I just a built a Desktop PC and installed Ubuntu. Its been up and running fine so far. But I just realized that one of my internal disk drives is not being utilized.


I have one 250gb ssd drive, the OS is currently installed here
and a 2tb SATA internal harddrive, this drive is currently not being recognized (screenshots from gparted is attached)


Please advise on how to add the second harddrive
How to plan space allocation (i.e. what files/folders should reside on SSD versus internal harddrive)
I intend  to install windows eventually on this PC too (maybe as dual boot or on VM)


Please advise


Thanks

[ATTACH=CONFIG]270681[/ATTACH]

[ATTACH=CONFIG]270683[/ATTACH]
[ATTACH=CONFIG]270682[/ATTACH]

---

### Post by Bucky Ball on 2016-08-13
Welcome. Good to hear this is your only issue and is easily fixed. 

Click on the unallocated space, go to 'Devices' in the drop down menus along the top bar and 'Create Partition Table'. You want to write a new partition table.

Once this is done, right click on the unallocated space and 'New'. Create partitions as required.

You will need help to get them mounting how you like. Let us know when you get there ...

---

### Post by kiranshri on 2016-08-14
Thank you, How do i decide how many partitions I require?

---

### Post by oldfred on 2016-08-14
Partitioning is very personal.
Or what I need may not be what you need.

I often find the partitions I want, will be different a year or two later, but I only keep a main working drive for about 3 years before it gets demoted to data only/backs, so new drive gets new partitioning.

 Oldfred's current partitions Dec 2015 - note neither drive is fully partitioned yet. Usually I just install another copy of Ubuntu or some temporary space for data.
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413) 

Note I have SSD & HDD with gpt partitioning and UEFI boot. You showed the 35 year old BIOS/MBR configuration.
Windows will only install to MBR partitioned drive in BIOS boot mode and you must then boot Windows installer in BIOS mode to install in BIOS mode.

      
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

