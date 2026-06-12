---
title: "Best use of a 128GB SSD for Ubuntu"
date: 2013-12-21
forum: Installation &amp; Upgrades
---

### Post by Photobug on 2013-12-21
I have gotten my HTPC home theater PC up and running with Ubuntu 12.04 and was contemplating trying to run a second OS (Hackintosh) alongside it but am pretty happy the way Ubuntu with XBMC is running but find myself using the Ubuntu more on its own.  Currently I have the setup on a 250 GB HDD and am running all my media on a collection of thumb drives and flash cards I plug into the HTPC when I want to watch or listen to something.

I want to finalize the install and upgrade in a different configuration using an 128 GB SSD I would to run the OS and am looking for suggestions to format the SSD to accommodate a flexible and secure Ubuntu setup?  

I have the potential for 3 other HDDs in the computer (I don't need to use them all but have the space an HDDs if it would help)

[LIST=1]
[*]The current OS HD at 250GB
[*]A 500GB HDD
[*]An old laptop HDD as another source for an OS operator
[/LIST]

What I would like to do is migrate my current OS to the SSD and allow room for two more versions of Ubuntu on the SSD as well.  One as a secure backup and one as a place to experiment with.

Here is a link from TheFU in a thread that OldFred suggested as a way to dualboot from, but that is for a different computer I am working 
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[COLOR=#008080]
The real advice you need is about HDDs and partitioning to make running lots of different OSes as easy as possible.
* Use GPT partitioning, If you won't run any old Linux or WinXP directly  on the hardware. The wikipedia article explains lots. For you and me,  GPT means never running out of partitions, having access to more than  2TB of storage, and having redundant copies of the partition table at  opposite ends of the physical disk.
* Partitioning - leave room for later. No need to allocate all the storage up front.
** 60G for Windows OS and Apps - NTFS
** 200G for User Data under Windows  - NTFS
** 20G x 5 for different Linux installs.  20G is overkill, but ... 10G  usually is not quite enough. Maybe 5x15G is the middle ground?
** 2G for swap or 1.5x your RAM if you plan to use "hibernate" - this swap will be shared by all Linux installs
** 10G-100G for /home ... somewhere around 20G is probably enough.  You  can share /home across all the Linux installs too, if you like, but  understand that different GUI environments can step on each other, so  you might want to setup different userids for each environment that you  test ... until you decide.
** 500G-3+TB - /Data   This is for big media files - no programs, just  data. Make it NTFS so both Linux and Windows can have easy access to it.  Do not allocate all of this up front. It will be nice to be able to  increase the size of other partitions by 10G, if you outgrow the initial  allocation. If you leave 10G of space free between every partition,  you'll have some great flexibility in the future. Just a thought.
* I do not use SSDs. I'm not comfortable with the lifespan of those devices yet. I'm probably overly cautious.
* Whatever disks you buy, make sure you have at least that size available so you can backup stuff.
* Put the swap on a different physical disk from the OS.
* Put your data and /home on a different physical disk from the OS.

If you dno't think you'll have 5 Linuxen installed at once or you plan  to use virtualization instead, change the 5x to 2x ... it is always very  useful to have storage for 2 versions of Linux on a big box like this.  You will still need storage for the VMs, but you can put it anywhere  inside a normal Linux partition.

The selection of a Linux file system isn't all that critical - if you don't know or don't care, use ext4.[/COLOR]

[LIST]
[*]How best can I configure the SSD to accept a copy of my current system with space for other Ubuntu experiments?
[*]How  best to configure up to 3 other HDDs to work with this system to keep a  backup OS and Data the most stable?  The systems and Data will be  backed up externally on occasion.
[*]Should I use GParted to configure the SSD and HDDs then clonezilla to migrate the OS over?
[/LIST]

---

### Post by oldfred on 2013-12-22
If the SSD is to be just a boot drive you can put 5 to 10 / (root) partitions on the drive. I have a 60GB SSD with two / (root) one current and one future. My current root also has /home and uses about 10GB of the 25GB and 2GB of that is .wine for Picasa in /home. My test install uses a lot less. You can make each / 10 to 25GB if you are keeping data on other data drives.

I use gpt for all new drives, but boot with BIOS. I started with gpt on one drive and Windows in MBR on another drive with 10.10. Only use MBR if you want Windows on a drive and only have BIOS to boot with. UEFI needs gpt for both Windows & Ubuntu.
I also add an efi partition only since I had planned on later moving my SSD to a new UEFI computer and putting the efi partition first later would be difficult to reorganize.

I prefer clean installs and copy the hidden /home folders & files you need for the user configuration. All data then is on rotating drive.

I prefer to use gparted but also have gdisk. And you must have the bios_grub if booting with BIOS.
       If using gpt with BIOS create a 1MB bios_grub partition with no format.
 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

    
sudo apt-get install gdisk
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by Photobug on 2013-12-22
> **oldfred said:**
> If the SSD is to be just a boot drive you can put 5 to 10 / (root) partitions on the drive. I have a 60GB SSD with two / (root) one current and one future. My current root also has /home and uses about 10GB of the 25GB and 2GB of that is .wine for Picasa in /home. My test install uses a lot less. You can make each / 10 to 25GB if you are keeping data on other data drives.

I use gpt for all new drives, but boot with BIOS. I started with gpt on one drive and Windows in MBR on another drive with 10.10. Only use MBR if you want Windows on a drive and only have BIOS to boot with. 


Thanks again OldFred for you help.  Unfortunately most of it went way over my head.  I have found and read up on GParted and feel comfortable in using it to format and partition the SSD and 500 GB HD.  

My plan on the SDD is to make 4 /root partitions with 5 GB of unallocated space between to expand if needed.  The rest of it will be partitioned to add a Windows later if needed. 
20GB
15GB+5 unallocated
10GB+5 unallocated
10GB

The remaining 63xGB left for a future other OS.

Should I put the /home, /swap on the HDD?  Is there a step by step guide on how to assign these partitions to specific functions?  Is it done during install using "Do something else"?

I don't know if this makes a difference but my motherboard is a  Gygabite GA-H67MA-UD2H-B3
Hybrid EFI technology with DualBIOS for 3TB HDD support

---

### Post by oldfred on 2013-12-22
You can create /home and swap on hard drive if you want. I keep /home on SSD inside my / (root) as I want different configurations but all the same data. I am aggressive in moving data but not the configurations that are mostly the . or hidden user configuration files & folders. Some larger configuration folders that have lots of data like Firefox and Thunderbird profiles I also move to data partitions.

There are a lot of threads on where swap should be. If you have 4GB or more or RAM it really will not matter as you rarely if ever will use it. You can share swap as long you you do not hibernate nor encrypt /home which also encrypts swap.

Windows will only boot from a gpt partitioned drive with UEFI. If thinking about Windows you need to use MBR partitioning, but then have the 4 primary partition limit. Or install Ubuntu in UEFI to begin with, but some of the older motherboards had limited UEFI that may not work well.

During install you assign, & format partitions. If not created in advance you also can create them, but I prefer to create in advance with gparted.
With manual install you also get to chose where to install grub boot loader and you want it into the MBR of the same drive as Ubuntu if BIOS. Or in efi partition if UEFI. But with UEFI you still specify sda or sdb. 

How you boot installer is how it will install UEFI or BIOS.

---

### Post by Photobug on 2013-12-23
So since I will be looking to potentially add windows to the setup down the road.  I will use MBR to partition the disk.  I will format it so there are 3 Linux sized partitions and one left over for Windows.


Which software should i use to create MBR partitions?

Another interesting thing came up though.  I had tried to run GParted on my USB live boot and it ran but just was not able to pull up any of the disks.  It spent 5 minutes "scanning all devices" before I just closed the app.

---

### Post by oldfred on 2013-12-23
Still use gparted. The default is MBR(msdos) partitioning.

Create a NTFS partition for Windows with the boot flag as sda1. Windows likes to be first, but can be any primary partition with MBR. Some have had issues when the primary partition for Windows is after the extended partition, so avoid that if at all possible.

I might leave a primary partition as unused, install one install in another primary and make the entire rest of drive as one larger extended partition. Inside the extended then you can have an unlimited number of logical partitions.

---

### Post by Photobug on 2013-12-23
> **oldfred said:**
> Still use gparted. The default is MBR(msdos) partitioning.

Create a NTFS partition for Windows with the boot flag as sda1. 

Got it.  I have been trying to look at my disk partitions with GParted using my live boot thumb drive and have gparted running but it is just "scanning for devices".  I thought using the live disk would be safer but it is unable to run gparted as far as I can tell.  I do no plan on altering the current HD that has Ubuntu running at all, should i just start up Ubuntu on my HD and use Gparted from in there to format the other two HDs?

---

### Post by oldfred on 2013-12-23
I like to have gparted on my hard drive to work on other hard drives. You just cannot use it to modify any mounted partitions which usually means your install and maybe all of your extended partition as swap would be mounted and that in effect mounts an entire extended if swap is a logical partition.

I have had issues where gparted does not find a drive. The newer versions of gparted seem to work better. My old XP would boot, but gparted would not mount that drive. It took forever & then timed out never showing my sda. I ran chkdsk on my NTFS partition and then gparted worked. (Windows booted in 3 min instead of 4 so that helped a little too). 

So if it is having issues chkdsk on NTFS or fsck on Linux partitions may be required. Or do you have any unually configurations like RAID or LVM? Gparted does not work with them currently. The very newest gparted as its own liveCD has added new features that may work with some other configurations.

---

### Post by Photobug on 2013-12-23
Thanks OF,
I had read up on GParted about a week ago and remembered it would not work on mounted disks and just figured it was best to run it from a live boot drive.  My live boot has a number of issues besides GParted needing solved but I will save that for a separate thread.  Since I did not need to work on the monted drive, I rebooted onto the HD installed Ubuntu and added Gparted and it worked like a charm.

I partitioned my 500 GB HD to have 30GB unalocated 200 and 250GB partitions.  A screenshot of the SSD partions is attached.  Next step is to try to install 12.04 to the SSD.  Will there be a problem if I leave the current HD running Ubuntu 12.04 plugged in?  I want to make sure this install does not corrupt or interfere with my current happy stable setup so I can revert back to it if needed.

[ATTACH=CONFIG]248843[/ATTACH]

---

### Post by oldfred on 2013-12-23
You have used all 4 primary partitions. If that is all you ever will want it is ok. But having an extended partition with logical partitions can give some flexibility in the future.

I do not disconnect other drives. Some suggest you do just to be safe.
If you only use Something Else and manually specify mounts -  /, swap, and if separate then /home, and formats like ext4, then you will not have any issues.
You do have to remember which partition is which. I have lots on my sdc drive and created several new ones at one time and installed to the wrong one. I had created a large data partition but installed system to it. Fortunately for me, I had not started to use data partition so I could just reinstall.
As soon as you have data you care about best to create good backup procedures.

---

### Post by Photobug on 2013-12-23
> **oldfred said:**
> You have used all 4 primary partitions. If that is all you ever will want it is ok. But having an extended partition with logical partitions can give some flexibility in the future.


I would like to confgure it to be the most flexible for future options.  I have recently learned about primary vs extended partitons but am not quite sure of the best way to use them to full advantage.  Will I be able to add the logical partitions in the do something else installation?  Right now I plan on just installing Ubuntu on sdc2.  Won't I still be able to configure all other partitions as needed as long as I do not install or store anything on them, if not how do you suggest I layout or partition the drive other than the sdc2 partion for best future options?

---

### Post by oldfred on 2013-12-23
The installer is not as flexible as gparted.
During install it will want a swap. If you plan on that on one of your hard drives you should also create that in advance.

I might recreate sda3 & sda4 inside an extended partition. The extended partition will then be sda3 as it also counts as a primary. And all logicals start at sda5, so current sda3 becomes sda5 and sda4 will become sda6.

If you want to try another way, you can also use fixparts. It lets you convert primary to logical, as long as you follow the partitioning rules. Main one is that all logicals must be inside the one extended.
       [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Fixparts is good to know about as it can do several things.

---

### Post by Photobug on 2013-12-23
[ATTACH=CONFIG]248852[/ATTACH]

Here it is based on your suggestions.  I decided to put the Swap on the SSD inside the extended partion, since I have more ssd than i know what to do with, I am hoping it will make it faster.  Although I have 4GB of ram and think it won't be used much.

---

### Post by oldfred on 2013-12-23
I have 4GB of RAM and almost never use swap. It will cache recent activity in RAM so it may seem that your RAM is full, but only if currently active programs are using all the RAM is then swap used. There also are settings to make it not use swap as much.  If you do video editing or typically load every program you have without closing any, then you may need swap.

       Trim in 14.04
[https://launchpad.net/ubuntu/+source/util-linux/2.20.1-5.1ubuntu11](https://launchpad.net/ubuntu/+source/util-linux/2.20.1-5.1ubuntu11)
HOWTO: Check If TRIM On Ext4 Is Enabled And Working On Ubuntu And Other Distributions
[http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking](http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking)
Ubuntu Aims To TRIM SSDs By Default
[http://www.phoronix.com/scan.php?page=news_item&px=MTUxOTY](http://www.phoronix.com/scan.php?page=news_item&px=MTUxOTY)
Trim as cron job, also must be ext4
[http://www.howtogeek.com/176978/](http://www.howtogeek.com/176978/)

    
I converted from discard in fstab to a cron job. Mine runs daily.
  trim does need ahci in BIOS
kernel version >=2.6.33. It does not work with ext3; (10.04 was 2.6.32)

   Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)
gksu gedit /etc/cron.daily/trim
sudo chmod +x /etc/cron.daily/trim


 #!/bin/sh
# trim
LOG=/var/log/trim.log
echo "*** $(date -R) ***" >> $LOG
fstrim -v / >> $LOG
# fstrim -v /home >> $LOG

I then get this:
```
*** Sun, 22 Dec 2013 08:06:13 -0600 ***
/: 18481389568 bytes were trimmed
*** Mon, 23 Dec 2013 07:51:34 -0600 ***
/: 2165702656 bytes were trimmed 


```

       Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://wiki.debian.org/SSDOptimization?action=show&redirect=SSDoptimization](http://wiki.debian.org/SSDOptimization?action=show&redirect=SSDoptimization)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by Photobug on 2013-12-26
I have been trying to respond to this over the last few days on my Windows laptop but it froze 3 times, so I have switched to my Ubuntu HTPC to get the job done.

> **oldfred said:**
> I have 4GB of RAM and almost never use swap. It will cache recent activity in RAM so it may seem that your RAM is full, but only if currently active programs are using all the RAM is then swap used. There also are settings to make it not use swap as much. If you do video editing or typically load every program you have without closing any, then you may need swap.

The first paragraph made sense to me not so much the second one, it made me consider posting my next thread in the beginner section where they use smaller words and less coding.  I assume it concerns the SSD special needs in Ubuntu.   
 

 So based on this thread I shrunk my Swap space to 2 GB and ran the installer with a fresh copy of a Ubootin as my last thumb drive was acting strange.  At first it froze then would only boot to the old HDD installed OS.  I was stumped and was about to post for help.  I went back to my previous post to see what kind of code I can run in Terminal to produce a report to help troubleshoot this and came across a boot repair that you helped me fix.  I ran the boot repair and I now have a working copy of Ubuntu on my SSD, I guess I have learned enough to leave the absolute beginner forum, thank you oldfred.
 

 Here are the details of my install.  I ran the install using “something else”.  In the live boot mode my 500GB HD was not recognized so I was not able to put some of the things I would have liked on there.  Mostly a “data” and the swap space.  I will get to that later.  After the install I used I consider this almost solved, just need help with a few more tweaks until I consider this install a done deal.
 

 So I got it working nicely and then ran through the steps here
 [https://sites.google.com/site/easylinuxtipsproject/first](https://sites.google.com/site/easylinuxtipsproject/first)
 and here [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)
 to configure my install and optimize my SSD.
 

 These are my last tweaks I would like to make:
 

 Because my storage HDD was not recognized during install (it is recognized now though by the SSD mounted Ubuntu)  I was not able to put my swap or data on it.  How do I relocate these to the sdb2 partition?  Should I make it an extended drive and add subpartions for swap and data on sdb2?

 

 On startup it gives me a lot of options to use the many different variations and locations of Ubuntu.  Can I cause it to open up the most recent kernel of Ubuntu on sdc2, but use a keyboard shortcut on startup to override that if I want to choose other options?

---

### Post by oldfred on 2013-12-26
If you have space and an extended partition to add more logical partitions you can create your swap and data partitions. If the extended is not mounted you can use gparted from your install on the SSD. But once you mount them later, then you can only use a live installer version. Installs do not normally have gparted, so you have to isntall it. 

Then you need to find the UUIDs and add entries into fstab for swap & data. With a data partition you have to create your own mount point and assign ownership & permissions to use it. 

Reference.
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Specific entry & examples.
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

I do not think above shows swap. This is mine (my data partition is old and still ext3, I would suggest ext4 now):

# swap was on /dev/sdc11 during installation. Of couse you have to use your UUID. (# is comment in fstab).
      
 sudo blkid -c /dev/null -o list
    
```

# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05 /mnt/data ext3 relatime 0 2
# swap was on /dev/sdc15 during installation
UUID=09367687-86d1-4fd0-9b81-2787d3196159 none            swap    sw              0       0
```

---

