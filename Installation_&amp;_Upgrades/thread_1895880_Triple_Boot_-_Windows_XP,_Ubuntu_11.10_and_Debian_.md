---
title: "Triple Boot - Windows XP, Ubuntu 11.10 and Debian 6"
date: 2011-12-15
forum: Installation &amp; Upgrades
---

### Post by websmoken on 2011-12-15
I have windows on a 180GB drive and Ubuntu is on a 250GB drive.  I would like to keep windows on it's own drive and repartition the 250GB for Ubuntu and Debian to reside.
What I need is a good partitioning scheme  using the primary, extended and logical and mount points.  I have the g-parted live CD and of course the install discs.

Thanks for all the help in advance.

        websmoken

---

### Post by oldfred on 2011-12-15
I will offer my suggestion, but partitioning depends on what you want to do, and even my own best partitioning is not so good after a year or two as I have changed what I want.

I like small system partitions and large data partitions. For example for your Windows I would have only 50GB for Windows and have the rest of the drive as NTFS data/shared partition. It helps avoid writing into a system partition and preventing system issues.

For Ubuntu & Debian I would just use two 25GB / partitions and keep /home inside each. But then I have all my data in a /mnt/data partition. I like to keep one primary partition available so I would put both data & swap into the extended partition and use only sda1 & sda2 for systems.

Also if your 250GB drive will only be Linux and you are booting with BIOS you can use the new gpt partitioning instead of the 30 year old MBR(msdos). Macs, new UEFI systems & large drives use gpt now.

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)
Multiboot install with gpt & using gdisk
[http://ubuntuforums.org/showthread.php?t=1566090](http://ubuntuforums.org/showthread.php?t=1566090)

If drive is only going to be Ubuntu (never Windows), I would suggest using gpt not MBR as the partitioning scheme. You then do not have any logical partitions, they are all primary and it has a backup in case of problems. You do have to create a tiny bios_grub partition to correctly install grub2's boot loader to the drive.
If using gpt create a 1MB bios_grub partition at the beginning of the drive. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)
With upstart script 
[http://ubuntuforums.org/showthread.php?t=1771773&page=5](http://ubuntuforums.org/showthread.php?t=1771773&page=5)
HowTo: Create shared directory for local users (with bindfs). - sisco311
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by fantab on 2011-12-15
+1 for the post #2 above.

It is further suggested that install GRUB to the HDD where you will have Linux, that way you won't mess the Windows MBR. You can later instruct the BIOS to boot Linux  HDD first.

---

### Post by websmoken on 2011-12-17
Sorry I took so long in getting back as I've been reading up.
I don't do music or a lot of photographs.  I'm not a rocket scientist doing warp speed equations.  I just like using Dreamweaver (Windows) I Google stuff Firefox (Linux), Thunderbird mail (Linux) wifey loves the games on Linux and Windows.
[CENTER]Heres my g-parted info

Windows Drive[/CENTER]
/dev/sda1  fat32  HP recovery 5.46GB
/dev/sda2  ntfs   HP_Pavilion  180.84GB   boot 

[CENTER]Linux Drive[/CENTER]
/dev/sdb1  extended    18.63GB
   ~/dev/sdb5  linux-swap 4.66GB
   ~/dev/sdb6  /     37.25GB
/dev/sdb2   /home  37.25GB
Unallocated        177.01GB

This is what the drives look like. lots of unused space on both. Can someone give me a good partitioning scheme for triplebooting? I've been with Ubuntu awhile but I'd love to be checking out Debian.

Thanks again for the help

[CENTER]Websmoken
[email]websmoken@comcast.net[/email][/CENTER]

---

### Post by oldfred on 2011-12-17
Ok, my partition example from sdc will be overkill as I have most of my Ubuntu installs still there (see labels) and two data partitions, one NTFS to share with xP and one ext3 for Linux data. I still have unallocated so I can add a 25GB / (root) in case I want to try something. You only need to add one or two 25GB / partitions and leave the rest for data.

My wife originally did not like Ubuntu and wanted XP. Then all the Thunderbird email & Firefox bookmarks were in XP, so while I was trying to learn Ubuntu I had to regularly reboot to XP. Once I put the Firefox profile & Thunderbird profile into a shared NTFS partition my wife could use Ubuntu for her email & web browsing. Much less rebooting into Windows.

---

### Post by fantab on 2011-12-17
> **websmoken said:**
> Sorry I took so long in getting back as I've been reading up.
I don't do music or a lot of photographs.  I'm not a rocket scientist doing warp speed equations.  I just like using Dreamweaver (Windows) I Google stuff Firefox (Linux), Thunderbird mail (Linux) wifey loves the games on Linux and Windows.
[CENTER]Heres my g-parted info

Windows Drive[/CENTER]
/dev/sda1  fat32  HP recovery 5.46GB
/dev/sda2  ntfs   HP_Pavilion  180.84GB   boot 

[CENTER]Linux Drive[/CENTER]
/dev/sdb1  extended    18.63GB
   ~/dev/sdb5  linux-swap 4.66GB
   ~/dev/sdb6  /     37.25GB
/dev/sdb2   /home  37.25GB
Unallocated        177.01GB

This is what the drives look like. lots of unused space on both. Can someone give me a good partitioning scheme for triplebooting? I've been with Ubuntu awhile but I'd love to be checking out Debian.


Here is what I have done with my /dev/sdb 500GB SATA:

```
/dev/sdb1 - 20GB - Primary - Ext4 - Oneiric Ocelot /
/dev/sdb2 - 20GB - Primary - Ext4 - Verne /
/dev/sdb3 - 20GB - Primary - Ext4 - Precise Pangolin /
/dev/sdb4 - xxxGB - Extended
/dev/sdb5 - xxxGB - Logical - Ext4 - Shared Data
/dev/sdb6 - 4GB - SWAP
```

**Ubuntu GRUB is installed on /dev/sdb and my BIOS is set to boot /dev/sdb first**.

I don't use /Home, as I prefer clean Installation of newer DISTRO versions instead of internal upgrade. So, I just format the 20GB partition and install the newer version whenever there is one available, without worrying about loosing Data on "Shared Data" partition.

---

### Post by xyzzyman on 2011-12-18
Oldfred is right that you will just like a different setup later. Here's my current FWIW (Single hdd in laptop)

My best recommendation is make a decision and then don't worry about it. I spent too much time moving things around instead of living life. :P If it works it works.

---

### Post by websmoken on 2011-12-30
Hi Guys

Sorry I've not gotten back sooner but have been in the hospital for the last week and a half.

I think we have enough info so as to make a decision on how to partition my drive.

Thanks to everyone for their input.

Web

---

