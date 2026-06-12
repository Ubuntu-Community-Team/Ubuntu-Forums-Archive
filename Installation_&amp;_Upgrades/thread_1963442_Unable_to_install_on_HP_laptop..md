---
title: "Unable to install on HP laptop."
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by PinkFloyd102489 on 2012-04-22
I recently purchased an HP dm4-3090se and tried to install Ubuntu on it. I've tried alt CD (hangs during install), Live CD (can't see correct partitions), and Wubi (installs, but won't boot, goes to busybox).

I'd really like to put Ubuntu or a variant on my laptop instead of running Windows 7 all the time, mainly for power saving reasons. I've also tried Linuxmint but gotten the same results.

Any help would be appreciated.

---

### Post by jerrrys on 2012-04-22
Wonder if you could do a terminal only install and then build to whatever.

And have you look into your graphics?  I have not looked myself, but you may find it helpfull.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Intel+HD+Graphics+3000&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Intel+HD+Graphics+3000&sa=Search&cof=FORID:9)

---

### Post by darkod on 2012-04-22
What do you mean by live cd can't see correct partitions? If you notice anything weird that might mean an error or corruption in the partition table. You need to sort it out first and consider installing only after that is sorted out.

Also, HP laptops usually come with all 4 primary partitions used, so the installer will not be able to create the ubuntu partitions unless at least one primary partition is deleted. But be careful which one you delete, ask first if unsure because it can break windows.

In any case boot into live mode first to see if there is any hardware incompatibility, and post the partitions layout if you think there is something wrong.

---

### Post by jerrrys on 2012-04-22
4 primary partitions

a Big +1

---

### Post by jadtech on 2012-04-22
first you should run checkdisk a few times rule out bad sectors causing problems ..

then win7 go to control panel in the search box type in partition click the link  there you  should be looking at partitions that are on your hard drive , if it shows 4 primary partitions  you are going to have to decide  which one to remove since  you cant have more then 4 to install ubuntu one needs to go on HP the one most choose to remove is one labeled hp tools..

once that is decided and done then you have to shrink volume on the partition with windows to free up space, I find 30 to 50GB  is enough but depending how big your HD and how full you might want more or less you have to leave enough for windows to still run ..

you do have to be careful when in this area to remove  a partition all you need to do is right click on the partition listed and on the menu choose delete to shrink the volume choose shrink ...

once you have done this put the ubuntu CD back in the drive and reboot and see how you install goes ..

---

### Post by PinkFloyd102489 on 2012-04-22
The unique thing about this laptop is it has a 20GB mSATA SSD, which is normally used as a caching scratch disk by Windows 7.

When I tried to install both Ubuntu and Linuxmint, I shrank the 2nd primary partition (where Windows is installed) down about 40GB in order to install Ubuntu. While in the partition manager, I can only see a 30GB partition, which is too large to be the mSATA and too small to be the partition I just created with the shrink.

As soon as my fiancee gets off of it, I'll look up the actual partition tables and post them.

---

### Post by jadtech on 2012-04-22
2 hard drives  i'm thinking this  might be of interest to you at least maybe point you in the right direction ..

[http://ubuntuforums.org/showthread.php?t=1959495&highlight=live+cd+raid+support](http://ubuntuforums.org/showthread.php?t=1959495&highlight=live+cd+raid+support)

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by PinkFloyd102489 on 2012-04-22
> **jadtech said:**
> 2 hard drives  i'm thinking this  might be of interest to you at least maybe point you in the right direction ..

[http://ubuntuforums.org/showthread.php?t=1959495&highlight=live+cd+raid+support](http://ubuntuforums.org/showthread.php?t=1959495&highlight=live+cd+raid+support)

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

There are two hdds, but I'm not installing a RAID.

The main disk is a 500GB drive. Current partitions are as follows:

199MB - System partition
447GB - C: (Windows partition)
16.85GB - D: (Recovery partition)
3.97GB - E: (HP_TOOLS partition)

I could probably do without the HP_TOOLS partition, but then I have no idea how to move the Recovery partition to the end of the drive and then adjust the free space for enough usable to install Ubuntu.

If it's the whole "There can be no more than 4 primary partitions", I can probably work around that. I may even end up installing Ubuntu to a persistent USB drive.

---

### Post by jadtech on 2012-04-22
i dont think you have to move the recovery partition  you just have to cut one partition shrink the one windows is on by what you want as long as the free space is in one big  chunk it can be any where on the drive ..

once you can get on live cd and see it using Gparted the way it is set up makes more sense :)

---

### Post by darkod on 2012-04-23
I believe there is an option to create restore DVDs with the software on the laptop too. In that case you can even delete both HP_TOOLS and the restore partition.

In any case, just deleting HP_TOOLS will do. You will need to open Disk Management in win7 and shrink the C: partition so that you create unallocated space for the ubuntu partitions. Shrink it for as much as you plan to use for ubuntu.

After that the install should go fine. Ask if you have any doubts.

---

### Post by mastablasta on 2012-04-23
> **PinkFloyd102489 said:**
> There are two hdds, but I'm not installing a RAID.
 

 
i wonder if there are really 2 hdd's as now they also sell hybrid HDD with SSD attached on top of disks.

---

### Post by PinkFloyd102489 on 2012-04-23
> **mastablasta said:**
> i wonder if there are really 2 hdd's as now they also sell hybrid HDD with SSD attached on top of disks.

According to the specs, it's a dedicated mSATA SSD. I'd really like to use that as the boot drive but don't want to take it away from Windows 7. The laptop runs fast enough that I wouldn't really need that anyway.

I know how to repartition, I'm just uneasy about deleting recovery partitions, as I've had bad things happen in the past without any way to recover.

I'll look into creating a recovery CD or see if HP can send me some. Thanks for all of the input. :)

---

### Post by jadtech on 2012-04-23
you dont have to delete the recovery partition at all , deleteing the hp tools is ok  not a problem and if you find later you really need it the info on that partition is down loadable on there sight .. 
recovery cd would be a good Idea you can make up to 2 copys right from windows ..

just know that as far as I read the recovery back up is also limited as well so  it is always good to make your own recovery back up ..

---

### Post by jadtech on 2012-04-23
> **mastablasta said:**
> i wonder if there are really 2 hdd's as now they also sell hybrid HDD with SSD attached on top of disks.

I think you could be right on this from all the details I can find for this HP online and I know not all have to be the same whatI find is it says it has a 500GB HDD and 20gb ssd that windows uses as a cache .

some of the decription I have read sell it as more of a built in flash drive or memory cache ..

---

### Post by PinkFloyd102489 on 2012-04-23
> **jadtech said:**
> I think you could be right on this from all the details I can find for this HP online and I know not all have to be the same whatI find is it says it has a 500GB HDD and 20gb ssd that windows uses as a cache .

some of the decription I have read sell it as more of a built in flash drive or memory cache ..

Technically, that's what it is in it's current setup. According to HP, it can be repartitioned into a boot configuration, much like I have my desktop setup. SSD boot drive with a secondary platter drive for storage use.

---

### Post by PinkFloyd102489 on 2012-04-23
So after deleting the two unused partitions and checking in Gparted, here's what I found:

The mSATA and hdd are indeed somehow RAID'd together. I'm not sure how, but Gparted is still showing no significant free space. I made 50GB available on the hdd, but it does not show.

[IMG]https://www.dropbox.com/s/qs97nei4hgueqto/2012-04-23%2018.08.33.jpg[/IMG]

[IMG]https://www.dropbox.com/s/ii1kx00guwug21i/2012-04-23%2018.08.45.jpg[/IMG]

---

### Post by jadtech on 2012-04-23
i believe you are going to have to  make the alternate CD for install to deal with  Raid

[http://releases.ubuntu.com/11.10/](http://releases.ubuntu.com/11.10/)

also you may not be able to see the free space because it may have never  shrank the volume . now that you dont have 4 primary partition  go to windows do a disk check on boot defrag  and  try to reduce the volume again  ..

if the numbers add up and the 50 gb is not missing from the window partition it is possible it couldnt shrink the volume  ..

remember when reducing from windows 50000 would be 50 gb

---

### Post by darkod on 2012-04-24
> **PinkFloyd102489 said:**
> So after deleting the two unused partitions and checking in Gparted, here's what I found:

The mSATA and hdd are indeed somehow RAID'd together. I'm not sure how, but Gparted is still showing no significant free space. I made 50GB available on the hdd, but it does not show.

[IMG]https://www.dropbox.com/s/qs97nei4hgueqto/2012-04-23%2018.08.33.jpg[/IMG]

[IMG]https://www.dropbox.com/s/ii1kx00guwug21i/2012-04-23%2018.08.45.jpg[/IMG]

I think it's time to post the output of the partitions. Boot into live mode, open terminal and post the output of:
sudo parted /dev/sda print all

That should show all disks and partitions.

I don't expect to see raid since it's pointless to raid a 500GB disk with a much smaller one. In raid, especially hardware raid or fakeraid, you use disks with same capacity.

---

### Post by PinkFloyd102489 on 2012-04-24
My images didn't show up for some reason, here are the image links of my partition tables.

[http://i.imgur.com/gwTT0.jpg](http://i.imgur.com/gwTT0.jpg)

[http://i.imgur.com/Dt2l8.jpg](http://i.imgur.com/Dt2l8.jpg)

---

### Post by PinkFloyd102489 on 2012-04-24
> **PinkFloyd102489 said:**
> My images didn't show up for some reason, here are the image links of my partition tables.

[http://i.imgur.com/gwTT0.jpg](http://i.imgur.com/gwTT0.jpg)

[http://i.imgur.com/Dt2l8.jpg](http://i.imgur.com/Dt2l8.jpg)


These were taken AFTER I deleted the HP_TOOLS and Recovery partitions on the platter drive.

---

### Post by darkod on 2012-04-24
Both partitions are still there, so something went wrong during the delete.

And the partitions not being displayed might be an error or corruption in the partition table. That's why I asked for parted output, not from Gparted.

In live mode open terminal, and post the output of both of these commands:
sudo fdisk -l (small L)
sudo parted /dev/sda print all

That will give text output including the start/end sectors of the partitions. More info than Gparted shows.

---

### Post by PinkFloyd102489 on 2012-04-24
Sorry, I had taken that Gparted shot before you asked.

Here's the output:

```
Disk /dev/sda: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe6000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x99e03f5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sdb2          409600   933097471   466343936    7  HPFS/NTFS/exFAT
/dev/sdb3       933099520   968433663    17667072    7  HPFS/NTFS/exFAT
/dev/sdb4       968433664   976764927     4165632    c  W95 FAT32 (LBA)

```

```
sudo parted /dev/sda print all
Error: /dev/sda: unrecognised disk label
```

```
sudo parted /dev/sdb print all
Model: ATA Hitachi HTS72755 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  210MB  209MB   primary  ntfs         boot
 2      210MB   478GB  478GB   primary  ntfs
 3      478GB   496GB  18.1GB  primary  ntfs
 4      496GB   500GB  4266MB  primary  fat32        lba


Error: /dev/sda: unrecognised disk label                                  

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
```

---

### Post by darkod on 2012-04-24
Well, I guess you see the results yourself.

You still have all four primary partitions on the 500GB disk, /dev/sdb. There are no partitions deleted.

And it says it can't find a valid partition table on /dev/sda but it does recognize it as 32GB disk.

If you have information to recover from /dev/sda you can try. If not, you can simply write new msdos table and you can use it.

---

### Post by PinkFloyd102489 on 2012-04-24
This is what Windows sees:

[IMG]http://i.imgur.com/TWijN.jpg[/IMG]

---

### Post by Dngrsone on 2012-04-24
[Here](http://linux.aldeby.org/post/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html) is a useful site for DV-4 installs.  I am not familiar with your drive configuration and can't help you there.

I have noticed that the CD sometimes hangs when booting up to the default screen, but if you hit a key when the little keyboard shows on the splash during bootup, you can get things going a but faster.

---

### Post by darkod on 2012-04-24
Hmm, weird.

Was the 32GB disk showing up in windows before? It's not shown in windows either. Do you have any data on it worth saving or we can simply write new blank partition table?

As far as the 500GB disk is concerned, you can try deleting partitions #3 and #4 with parted too. It seems there is some confusion and parted still shows them.

For example, if you decide to do it, in live mode in terminal it would be like:
To enter parted prompt:
sudo parted /dev/sdb

To print the current partitions:
print

If # and ~are still there, to remove them:
rm 4
rm 3

Print again to see if they are gone:
print

Exit parted prompt:
quit

That should be it.

In theory this should not affect windows at all. But in theory they shouldn't show different partitions list too. :)

---

### Post by PinkFloyd102489 on 2012-04-24
I was told by HP that Windows isn't able to see the mSATA SSD, that it only uses it as a caching disk. From looking at how the Ubuntu installer is wanting to activate a RAID instance. I'd say the mSATA and hdd are somehow in a JBOD config.

---

### Post by PinkFloyd102489 on 2012-04-24
I was stupid and forgot to shrink the space I wanted to install Ubuntu to.

However, I am not seeing the 50GB that I shrank on the main hdd (500GB).

---

### Post by jadtech on 2012-04-24
very interesting  though let me get this straight the whole issue is because Gparted   & live cd can see both drives  while windows cant ..

---

### Post by PinkFloyd102489 on 2012-04-24
> **jadtech said:**
> very interesting  though let me get this straight the whole issue is because Gparted   & live cd can see both drives  while windows cant ..

They can see both drives, but cannot correctly display the partition tables.

The Ubuntu installer can only see /dev/sda, with no tables. sdb does not even exist, so I cannot install to it, according to the installer.

---

### Post by darkod on 2012-04-25
If they are really in JBOD that might explain why linux is displaying different partitions.

The smaller, /dev/sda, seems to not have a partition table recognizable by ubuntu. This is easy to sort out by writing a new one. But I have no idea how that would influence windows, and how it's set up.

I would say you have a great change to use the 32GB SSD for ubuntu only, it should fly on that (depending on the spec of the SSD). But that would mean you will have to find a way to "break" the JBOD, and tell windows not to use it in some way.

It is very strange that the 32GB doesn't even appear in windows. No matter how it's used, shouldn't it be there as a device at least.

---

### Post by PinkFloyd102489 on 2012-04-25
> **darkod said:**
> If they are really in JBOD that might explain why linux is displaying different partitions.

The smaller, /dev/sda, seems to not have a partition table recognizable by ubuntu. This is easy to sort out by writing a new one. But I have no idea how that would influence windows, and how it's set up.

I would say you have a great change to use the 32GB SSD for ubuntu only, it should fly on that (depending on the spec of the SSD). But that would mean you will have to find a way to "break" the JBOD, and tell windows not to use it in some way.

It is very strange that the 32GB doesn't even appear in windows. No matter how it's used, shouldn't it be there as a device at least.

It's actually a 20GB mSATA SSD and a 500GB 7200rpm HDD. So I'm assuming that the reason the partitions are screwed is due to the JBOD, not the actual drive capacities.

While this is a fantastic laptop and it has everything I want, this is slightly a deal breaker. I might return it and wait for something in a different brand that would actually allow me to install Ubuntu without hassle.

---

### Post by AZ_RUNE on 2012-04-25
> **PinkFloyd102489 said:**
> While this is a fantastic laptop and it has everything I want, this is slightly a deal breaker. I might return it and wait for something in a different brand that would actually allow me to install Ubuntu without hassle.


Please don't return it you have the exact laptop I am looking at getting and I am going to wipe and install Win7 and Ubuntu fresh as dual boot. I am thinking of taking 12GB of the 32GB drive and letting Windows use it for ready boost. I then want to take the remainder and use it for Ubuntu and load the /home and swap partitions to the platter drive alongside the Windows install.

Thoughts?

AZ_RUNE

---

### Post by darkod on 2012-04-25
This is what one review about HP dm4 says:
> Thanks  to its 20GB SSD cache (which is not user-accessible), this HP notebook  posted a fast boot time of 43 seconds -- 20 seconds faster than the  63-second category average. The XPS 14z and its 750GB 7,200-rpm  hard-drive booted Windows in 60 seconds, while the N43SL and its 750GB  5,400-rpm hard drive loaded in a sluggish 84 seconds.

They also note that recent models are shipped with 32GB not 20GB.

I guess the "not user-accessible" might refer to windows use. If ubuntu can see a 32GB /dev/sda device, and it can, I see no reason why you wouldn't be able to use it.

The problem is you would have to locate how windows uses it (page file? readyboost device?) and "kill" that option. That way if you install ubuntu on it, you can hope windows not to break.

You can try writing a new msdos table on it and install ubuntu, but if you don't investigate how windows uses it first, it might break windows functioning.

---

### Post by PinkFloyd102489 on 2012-04-25
> **darkod said:**
> This is what one review about HP dm4 says:


They also note that recent models are shipped with 32GB not 20GB.

I guess the "not user-accessible" might refer to windows use. If ubuntu can see a 32GB /dev/sda device, and it can, I see no reason why you wouldn't be able to use it.

The problem is you would have to locate how windows uses it (page file? readyboost device?) and "kill" that option. That way if you install ubuntu on it, you can hope windows not to break.

You can try writing a new msdos table on it and install ubuntu, but if you don't investigate how windows uses it first, it might break windows functioning.

It boots faster than 43 seconds.

Interesting though, now I've changed my mind about the JBOD. I'll investigate how it's being used. If I can partition a little bit of the SSD while maintaining it's functionality, that would make me very happy.

---

