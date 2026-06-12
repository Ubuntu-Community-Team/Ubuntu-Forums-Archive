---
title: "Dual boot across 2 hard drives?"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by aaron94 on 2010-05-04
Hello, I'm new to these great forums and have a question:

I would like to install Ubuntu 10.04 on my new 1 TB hard drive. I currently have Windows XP installed on a 160 GB hard drive for things that I cannot do on Ubuntu. 

I would like to know if it's possible to install the other hard drive, and then dual boot Windows with it? Effectively dual booting across two hard drives. I wouldn't care if GRUB replaces the standard Windows bootloader, just as long as I can choose between the two at startup :) 

Does anyone know if it's possible to do this? Thanks in advance :)

---

### Post by ubername on 2010-05-04
Yes, you can do it easily. Just select the second hard drive in the partition step  of the install.

---

### Post by aaron94 on 2010-05-04
Ok, just wanted to make sure that GRUB doesn't get installed to the wrong hard drive and won't let me boot at all....

---

### Post by oldfred on 2010-05-04
When you do the install you need to use the advanced button and make sure to choose the 1TB drive (probably sdb)  to install grub to. Then in BIOS switch boot to the 1TB drive. You should be able to switch back at any time and directly boot windows. If necessary it is not difficult to reinstall a windows boot loader or grub to sda  or sdb as required. It is generally better to have grub on the same drive as the Ubuntu install. If the install does not immediately find windows sudo update-grub should find it.

---

### Post by tsucol11 on 2010-05-04
> **aaron94 said:**
> Hello, I'm new to these great forums and have a question:

I would like to install Ubuntu 10.04 on my new 1 TB hard drive. I currently have Windows XP installed on a 160 GB hard drive for things that I cannot do on Ubuntu. 

I would like to know if it's possible to install the other hard drive, and then dual boot Windows with it? Effectively dual booting across two hard drives. I wouldn't care if GRUB replaces the standard Windows bootloader, just as long as I can choose between the two at startup :) 

Does anyone know if it's possible to do this? Thanks in advance :)

I agree with Oldfred. I am running XP pro my primary 360gig HD and Ubuntu 10.04 from my secondary terabyte drive.

Grub is installed on the second (terabyte)drive. When my computer boots up (ASUS motherboard) I simply press F8 to select which HD I want to boot off from. 

This way I can reinstall, delete .... either operating sytem & still be able to boot.

Brian

---

### Post by aaron94 on 2010-05-04
If I do it the way you are saying to do it (put GRUB on TB hard drive) will GRUB start when I boot? And can I select Windows or Ubuntu from that list? That is what I would like to be able to do.

Thank you guys very much for the quick responses and great help :)

---

### Post by wausaubill on 2010-05-04
Actually, what I think the previous posters are saying is that you will not select which OS to boot with GRUB.  Yes, if you set your 1TB drive as the boot drive, GRUB will normally run and boot Ubuntu.  If you want Windows, you will have to intervene, and change your boot drive in the BIOS.

Bill

---

### Post by aaron94 on 2010-05-04
Any way to have it show Windows and Ubuntu in GRUB just like a normal dual boot on one hard drive?

---

### Post by oldfred on 2010-05-04
Grub2 is very good at finding other operating systems (that are working) and letting you boot them. When you have different boot loaders in different MBRs you can use the one time boot key (f12 on my system) to choose.  But, if in BIOS you make the 1TB drive first to boot then you can choose in the grub menu any operating system you have installed on any drive. Of course you can switch BIOS back or one time boot directly if you want.

I have 3 versions of Ubuntu & XP. They all show up in grub2. But I have different boot loaders in each drive, but set BIOS to boot sdc as that boots my main system first.

---

### Post by aaron94 on 2010-05-04
> **oldfred said:**
> Grub2 is very good at finding other operating systems (that are working) and letting you boot them. When you have different boot loaders in different MBRs you can use the one time boot key (f12 on my system) to choose.  But, if in BIOS you make the 1TB drive first to boot then you can choose in the grub menu any operating system you have installed on any drive. Of course you can switch BIOS back or one time boot directly if you want.

I have 3 versions of Ubuntu & XP. They all show up in grub2. But I have different boot loaders in each drive, but set BIOS to boot sdc as that boots my main system first.

So, you're saying that even if I have Grub installed on my terabyte hard drive, I can still boot Windows from it, which is on the other hard drive? I just need to set the terabyte hd as the primary drive then?

---

### Post by oldfred on 2010-05-04
It works great for most. For some there can be issues, which keeps us busy on the forums as Ubuntu seems pretty popular.

---

### Post by aaron94 on 2010-05-04
> **oldfred said:**
> It works great for most. For some there can be issues, which keeps us busy on the forums as Ubuntu seems pretty popular.

I guess I'll give it a try tonight, and give it a [SOLVED] if it works. 

Just to be clear, I'm installing this normally, but making sure that GRUB goes on the terabyte drive? That way, I'm still able to boot Windows from Grub? And, I'm also setting the primary boot drive to the terabyte one after the install too?

---

### Post by user333 on 2010-05-04
I would just like to warn you I heard that sometimes if you remove one of the hard drives the boot manager will go crazy and not work

I'm not sure if that is the case with grub
I have the same setup as you described and I just switch hard drives when I want to use windows
no messy software to deal with ;)

---

### Post by aaron94 on 2010-05-04
> **user333 said:**
> I would just like to warn you I heard that sometimes if you remove one of the hard drives the boot manager will go crazy and not work

I'm not sure if that is the case with grub
I have the same setup as you described and I just switch hard drives when I want to use windows
no messy software to deal with ;)

Switch hard drives.....from BIOS?

---

### Post by wilee-nilee on 2010-05-04
I think oldfred is on the button with this install, those of you offering alternative ways of doing it are used to another way, which is haphazard at best. You don't have to remove drives for installing or switch HD's for booting, any HD MBR can be overwritten with ease, generally. The screen shot is very helpful as well.

---

### Post by aaron94 on 2010-05-04
OK, /home partition is currently the whole terabyte....What other partitions do I have to setup and how large do I make them????

---

### Post by oldfred on 2010-05-04
Now you are into personal desires and for everyone posting I expect you to get several answers. It depends on what you plan to use the system for. My orginal install just had root & swap with a shared NTFS partition for some data that I shared between systems.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)


If you are thinking of additional operating systems you may want several extra 20GB partitions for roots & homes.

---

### Post by aaron94 on 2010-05-04
I'll allocate 10 - 15 GB for /, and for transferring files between the two I think I'll use my portable HD. Thanks for the help, oldfred! I don't need a /boot partition, do I? And I think /swap is out of the question, as I have 5GBs of RAM.

---

### Post by wilee-nilee on 2010-05-04
> **aaron94 said:**
> I'll allocate 10 - 15 GB for /, and for transferring files between the two I think I'll use my portable HD. Thanks for the help, oldfred! I don't need a /boot partition, do I? And I think /swap is out of the question, as I have 5GBs of RAM.

Swap will allow you to hibernate or suspend, so that is a personal preference, oldfred will have a better answer I suspect.

---

### Post by aaron94 on 2010-05-04
oldfred's method worked for me, thanks very much!!! :) I can boot Windows from GRUB on the 1TB hard drive!! Thanks guys, you were a great help! Solved.

---

