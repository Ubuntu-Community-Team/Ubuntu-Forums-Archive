---
title: "500GB HDD: Partition sizes + filesystems for Win8, Ubuntu, and media/program files?"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2013-05-04
Hi

My Asus Zenbook UX32 has a 500GB HDD and I would like to dual boot it. At the moment only a fresh install of Windows 8 exists on it, and I only have this so I can play games, and I use linux for almost everything else.

Unfortunately there is no way for me to predict how much room I will need for games, and how much I will need for media which it would be nice to be able to access from both OS but I could live with just being able to access it from linux. 

The main problem here is that I do not want to make any partition  either too small so I end up having to resize, or too large so that the  space is wasted and could be used somewhere else - media versus games.

Perhaps I should configure it with the following partitions: 


[LIST=1]
[*]Windows 8 comprising the operating system and essential software like security 
[*]NTFS partition where I can install Windows programs - mainly games - and store media 
[*]EXT4/XFS Ubuntu / (Which file system is best for the Ubuntu partitions?) 
[*]EXT4/XFS Ubuntu /home 
[*]EXT4/XFS Ubuntu /boot (I have read it can help to create a separate boot partition?)
[*]4GB Swap 
[/LIST]

Which of these partitions do I need to make primary, and which logical or extended? Also, for the non primary partitions please specify what primary partitions they are extended from. 

What size would you recommend for each partition?

If you believe I should be partitioning a different way please tell me. Like I said, being able to access media from both OS would be a nice bonus so I could use things like iTunes, if I were so inclined, but I would be happy enough just using linux as that is where I will be most of the time anyway - I could just then store all of my media on a very large /home partition, but then what to do about games and programs for windows?

---

### Post by oldfred on 2013-05-04
Is this Windows 8 that you installed so it is BIOS/MBR or pre-installed so it is UEFI/gpt partitioned?

Only a few systems need a separate /boot. They seem to have a BIOS that will only boot from the first 137GB of a drive. And it seems to be either very old systems or USB drives, and may be BIOS settings or a grub bug on the newer systems. If your system needs the /boot it has to be totally inside the first 100GB of a drive.

I would just use ext4 not any other format for Linux.
       Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

If you are going to have a large NTFS data partition, you may not need the separate /home. I often suggest the separate /home to keep data and user settings separate from main system to make it easy to reinstall. But if all data is in another partition, the mostly hidden user settings are tiny and easily backed up for a new install. 

You can only have one extended partition and it is just a container for all the logical partitions which must be inside it. It counts as one of the 4 primary partitions in MBR(msdos) partitioning. But inside it you can have essentially an unlimited number of logical partitions. Windows will read a logical partition formatted with NTFS, but does not see Linux partitions.

I often suggest 10 to 25GB for / (root). I use 25GB but actually only have used 9GB including my /home inside my /, but I have two data partitions, one NTFS from when I still booted XP and one Linux formatted where all new data goes. My NTFS still has my Firefox & Thunderbird profiles so I could have same bookmarks and email in every system I boot, both Windows and multiple Ubuntus.

Have not made iTunes work with Ubuntu, but I do copy photos from iPhone to my Linux without issue. I think I installed some extra drivers somewhere along the way.

---

### Post by Dáire Fagan on 2013-05-05
Thanks for the reply.

> **oldfred said:**
> Is this Windows 8 that you installed so it is BIOS/MBR or pre-installed so it is UEFI/gpt partitioned?

My UX32A came with Windows 7 but there was some problem with the operating system so I reinstalled Windows 7 from a USB flash drive and then I took the special offer to upgrade to Windows 8 online. I have since removed any remnants of the old operating system and also used Windows' 8 built in reset feature which removed everything from the drive and reset everything on it. 

Is there a way to check if it is BIOS/MBR or UEFI/GPT? I can access a linux terminal using Ubuntu Live if you want me to enter commands.

The Zenbook also came with several partitions ASUS had preconfigured, if you can tell me what command will show the most information I can post the output here.

> **oldfred said:**
> Only a few systems need a separate /boot. They seem to have a BIOS that will only boot from the first 137GB of a drive. And it seems to be either very old systems or USB drives, and may be BIOS settings or a grub bug on the newer systems. If your system needs the /boot it has to be totally inside the first 100GB of a drive.

Hopefully I do not need one then.

> **oldfred said:**
> I would just use ext4 not any other format for Linux.
       Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

EXT4 for root it is.

> **oldfred said:**
> If you are going to have a large NTFS data partition, you may not need the separate /home. I often suggest the separate /home to keep data and user settings separate from main system to make it easy to reinstall. But if all data is in another partition, the mostly hidden user settings are tiny and easily backed up for a new install.

So if I create and set the large partition to /home during Ubuntu install will that cause any problems installing Windows games somewhere on it to play while using Windows?

> **oldfred said:**
> You can only have one extended partition and it is just a container for all the logical partitions which must be inside it. It counts as one of the 4 primary partitions in MBR(msdos) partitioning. But inside it you can have essentially an unlimited number of logical partitions. Windows will read a logical partition formatted with NTFS, but does not see Linux partitions.

Okay, so Windows must be primary already, but what do I set the other partitions as?

> **oldfred said:**
> I often suggest 10 to 25GB for / (root). I use 25GB but actually only have used 9GB including my /home inside my /, but I have two data partitions, one NTFS from when I still booted XP and one Linux formatted where all new data goes. My NTFS still has my Firefox & Thunderbird profiles so I could have same bookmarks and email in every system I boot, both Windows and multiple Ubuntus.

I will set 20GB for root leaving lots of room for upgrades etc. Is swap to be set to 4GB? Sharing profiles for Firefox across multiple OS is very cool, but is it really necessary considering you can now do the same thing very easily with Firefox Sync? 

> **oldfred said:**
> Have not made iTunes work with Ubuntu, but I do copy photos from iPhone to my Linux without issue. I think I installed some extra drivers somewhere along the way.

If I really need to use it I can just install it on the NTFS large partition.

---

### Post by oldfred on 2013-05-05
Your /home cannot be the NTFS shared. NTFS is a Windows format and does not support ownership & permissions required for Linux security. Your /home does have all users data normally and the users settings for applications. Data is data, do it does not have to have the secuity settings and can be in the shared data partition. 

I do not think you can install any games in Windows and use in Ubuntu or vice-versa. 

Post this. Most Windows 7 systems use all 4 primary partitions. Do not attempt to create partitions in Windows as it converts to dynamic and that does not work with Linux.

       sudo parted /dev/sda unit s print

 Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by Dáire Fagan on 2013-05-06
> **oldfred said:**
> Your /home cannot be the NTFS shared. NTFS is a Windows format and does not support ownership & permissions required for Linux security. Your /home does have all users data normally and the users settings for applications. Data is data, do it does not have to have the secuity settings and can be in the shared data partition.

I am eager to start installing, so after you see the terminal output and GParted screenshots below [COLOR=#ff0000]**please clarify how exactly you are recommending I partition the drive for my requirements**[/COLOR], including the number of partitions, filesystems, partition sizes, and whether they should be primary, extended, or logical. Considering what you have said maybe I should go with a 20GB root, 50GB /home, 8GB Swap (RAM is 4GB), and use all the other space for the Windows 8 partition where I will install games - is there any reason I can not save and access media from the Windows partition while using Ubuntu? If instead you think it best I do something like limit the Windows 8 partition to 50GB or so and install games AND store data on a single separate NTFS partition please confirm this.

> **oldfred said:**
> I do not think you can install any games in Windows and use in Ubuntu or vice-versa.

I was not suggesting this though I think it actually is possible. I plan to play games on Windows for the moment, as despite all the extra tweaks for individual games over at WINEHQ the ones I play just run better while using it.

> **oldfred said:**
> Post this. Most Windows 7 systems use all 4 primary partitions. Do not attempt to create partitions in Windows as it converts to dynamic and that does not work with Linux.

It looks like I do not have 4 primary partitions for my Windows 8 install. There was a recovery partition for Windows 7 when I received my laptop but it became corrupted and ASUS would not send a recovery CD here to Ireland and there were no download options :( Windows 8 new built in reset feature does seem to work great though.

> **oldfred said:**
> sudo parted /dev/sda unit s print

Before looking at this output bear in mind I was running Ubuntu from a Live USB, and my laptop has an internal 24GB SSD drive for Intel Rapid Start Technology or Intel Rapid Storage Technology - I get them mixed up - which I still need to reconfigure manually.

```
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: Verbatim STORE N GO (scsi)
Disk /dev/sda: 15645120s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End        Size       Type     File system  Flags
 1      2048s  15645119s  15643072s  primary  fat32        boot

ubuntu@ubuntu:~$ sudo parted /dev/sdb unit s print
Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sdb: 976773168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start    End         Size        Type     File system  Flags
 1      2048s    206847s     204800s     primary  ntfs         boot
 2      206848s  976771071s  976564224s  primary  ntfs

ubuntu@ubuntu:~$ sudo parted /dev/sdc unit s print
Model: ATA SanDisk SSD i100 (scsi)
Disk /dev/sdc: 46905264s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start     End        Size       File system  Name                  Flags
 2      2048s     8390655s   8388608s                Basic data partition
 1      8392704s  46903295s  38510592s               HFS

```

[IMG]http://i.imgur.com/4xppqVf.png[/IMG]

---

### Post by oldfred on 2013-05-06
Your Intel SRT may confuse things.
It uses RAID and that leave meta-data on drives. It used to be that Ubuntu would not install, but it now seems to install, but then grub sees the RAID data and will not install as with RAID it does not install to MBR.
You may have to remove the RAID meta-data. 

Some want the speed with Windows and if you are a gamer I would think you would, but those that are primarily Ubuntu users install Ubuntu's / (root) to the SSD with /home or data on hard drive. Ubuntu then boots and runs fast but then Windows is not caching its data and is back to normal slow Windows.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)


 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

If dual booting, I do not recommend hibernating. And the only reason to have swap equal to RAM in GiB (not GB) is to hibernate. You might want to have 2GB just to have some, I have 4GB of RAM and have not seen it use swap with my normal work load.
      
 [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

What you have decided on partition sizes otherwise seems fine. I find my own optimal partition scheme is not so good a year or two later after I find I want to do something different.

---

### Post by Dáire Fagan on 2013-05-09
Hi oldfred, thank you for your support thus far, I am making slow but sure progress.

[COLOR=#ff0000]**Please answer a question anywhere you see a question mark.**[/COLOR]

> **oldfred said:**
> Your Intel SRT may confuse things.
It uses RAID and that leave meta-data on drives. It used to be that Ubuntu would not install, but it now seems to install, but then grub sees the RAID data and will not install as with RAID it does not install to MBR.
You may have to remove the RAID meta-data. 

Some want the speed with Windows and if you are a gamer I would think you would, but those that are primarily Ubuntu users install Ubuntu's / (root) to the SSD with /home or data on hard drive. Ubuntu then boots and runs fast but then Windows is not caching its data and is back to normal slow Windows.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)


 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

Let me just clarify a few things regarding IRST (and ISRT) and my system. The acronym IRST is unfortunately used for individual Intel technologies and the entire family of Intel Rapid Storage Technologies, and it causes much confusion:

 Intel Smart Response Technology - This accelerates the performance of a HDD using and SSD and RAID - This requires an SSD of 30GB+, an the option to select RAID in the BIOS (instead of either AHCI or IDE) which I do not have and as such my laptop does not support it. 

From a Dell guide:

> Smart Response is a feature that uses both a traditional hard disk drive (HDD) and a solid state drive (SSD) of greater than 32GB together.   It dynamically monitors file, data, and application use, and stores frequently used content on a special partition on the SSD device for faster access.  It provides SSD-like read/write performance for the files used most frequently, while providing lower overall storage cost by sorting and storing less frequently accessed content on the larger-sized traditional HDD. 


Intel Rapid Start Technology - This uses a hibernate partitioned part of an SSD greater or equal to the size of RAM to make the computer wake from sleep faster.

Dell:

> What is Intel® Rapid Start Technology? Rapid Start is a feature that provides power savings similar to Windows® hibernate state, while improving resume time vs. hibernate by ~2x.  Rapid Start may be combined with Smart Response on some systems to enhance overall system performance while also reducing power consumption when not in use. 


Intel Smart Response Technology (has own driver) and Intel Rapid Start Technology (has own driver) are features of Intel Rapid Storage Technology (has own driver), and there are other features too.

So on my laptop I have installed Intel Rapid Storage Technology and Intel Rapid Start Technology. I have partitioned the SSD, which for some reason appears as 22.37GB in diskmgmt.msc and 22GB in the IRStorageT control panel, with a 4GB hibernate partition for IRStartT, and I have mounted the remaining 18.36* into ExpressCache, another piece of software from Condusiv Technologies (formerly Diskeeper) that takes care of the caching instead of ISmartRT.

Anyway, because this is my set up instead of ISmartRT, I do not think it has negatively affected my Ubuntu installation at all[COLOR=#ff0000]**?**[/COLOR]

> **oldfred said:**
> If dual booting, I do not recommend hibernating. And the only reason to have swap equal to RAM in GiB (not GB) is to hibernate. You might want to have 2GB just to have some, I have 4GB of RAM and have not seen it use swap with my normal work load.
      
 [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Why is it you do not recommmend hibernating, that guide you linked does not mention dual booting or Windows (I searched by string) and it in fact mentions many reasons other than just hibernating for configuring swap**[COLOR=#ff0000]?[/COLOR]**

> **oldfred said:**
> What you have decided on partition sizes otherwise seems fine. I find my own optimal partition scheme is not so good a year or two later after I find I want to do something different.

What I have done is to remove all partitions before running a clean UEFI install of WIN8. I gave it 300GB onto which it automatically created 3/4 partitions. 

I then ran the Ubuntu 13.04 installer from a Live USB, selected the custom option, created a EXT4 20GB /, 8GB swap, and an EXT4 146GB, or whatever the remainder was, partition for /home. 

I figured I could install lots of games on the 300GB WIN8 partition and still have enough space in /home for media which will only be accessible from Ubuntu, and I cannot think of any good reason media from Windows anyway. Do you think a smaller partition of 20GB or so for /home and a new separate NTFS partition for media, Program Files, and Program Files (x86) would be better or cause problems somehow**[COLOR=#ff0000]?[/COLOR]**

After installing Ubuntu Windows would not boot so I installed and ran boot-repair which allowed me to select either Ubuntu, or Windows from GRUB although there are two Windows entries and they are messy - I will post a screenshot - do you know how I can correct the menu**[COLOR=#ff0000]?[/COLOR]**

Boot repair gave me some output to use when seeking support too and I will post it.

Boot-repair output:

[http://paste.ubuntu.com/5647921/](http://paste.ubuntu.com/5647921/)

It also told me the following:

> You can now reboot your computer.
Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/grubx64.efi file!

The boot files of [The OS now in use - Ubuntu 13.04] are far from  the start of the disk. Your BIOS may not detect them. You may want to  retry after creating a /boot partition (EXT4, >200MB, start of the  disk). This can be performed via tools such as gParted. Then select this  partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

There is no option in my BIOS to select I boot from sda2/EFI/ubuntu/grubx64.efi**[COLOR=#ff0000]?[/COLOR]**

Screenshots of GRUB menu and BIOS options to follow.

---

### Post by oldfred on 2013-05-10
If you can boot from entries ignore the location on drive. I do not think I have seen anyone with UEFI have that issue, but Boot-Repair reports it in case of an issue. Generally it was either BIOS setting, Old systems, or booting from USB hard drives that caused most of the beyond 100GB on drive issue.

I do not know details of the various Intel SRT versions. Most that have posted have SSD form 16GB to 32GB and many different brands and models. One or two have had dual SSD, but I do not know configuration.

Swap if just for RAM memory overflow if you launch too many apps at once. With my laptop with only 1.5GB I do see swap uses occasionally and I try not to load too many apps. With my Desktop and 4GB of RAM I do not use swap, but again do not see how many apps I can open at once. Some say they work without swap, but I think some is good, and others say it may boot a bit faster as it looks for swap and has to time out on not finding any. Not sure who is right. 
I do not hibernate, even before my SSD as it booted fast enough. Of course coming from XP with its 3 to 4 min boot anything is fast. 

I do not see an advantage to a small /home, if that is what you want then I would include it inside / and maybe make / larger. I use 25GB for / including /home but am aggressive in moving data & data folders into my data partitions, so my /home is only 2GB with 1.5GB for .wine. My wife uses the Windows version of Picasa in .wine and that takes some space. I put my Firefox & Thunderbird profiles in my shared NTFS so I have the same profile for all my installs. It is NTFS only to share with XP, but I do not now boot XP.

I do not know what files you see from UEFI menu, at top level you should have Windows and ubuntu as those are the folders in the efi partition. If using secure boot you boot Windows and that really is grub2's shim file renamed to Windows efi file name. Normally in ubuntu should be the grub file to boot.

---

### Post by oldfred on 2013-05-10
You can turn off os-prober until they fix the bug in grub2. And all the entries in 25_custom are from Boot-Repair.

# I add this line to grub configuration or turn off the execute bit on 30_os-prober
 gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executable bit
sudo chmod a-x /etc/grub.d/30_os-prober
# Then do:
sudo update-grub
Or one liner
 sudo echo GRUB_DISABLE_OS_PROBER=true >> /etc/default/grub 
sudo update-grub

   sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkup25_custom
gksudo gedit /etc/grub.d/25_custom
Then do:
sudo update-grub

---

### Post by Dáire Fagan on 2013-05-10
> **oldfred said:**
> If you can boot from entries ignore the location on drive.

Great, I would still like to clean up the entries in the GRUB menu though - please see the screenshot:

[IMG]http://i.imgur.com/IVZZJdk.jpg?1[/IMG]

[COLOR=#ff0000]**The  Windows entries seem to do the same thing. Is there anyway to remove  one of them and edit the name of one of the other to something neat like WIN8  or Windows 8?**[/COLOR]

> **oldfred said:**
> Swap if just for RAM memory overflow if you  launch too many apps at once. With my laptop with only 1.5GB I do see  swap uses occasionally and I try not to load too many apps. With my  Desktop and 4GB of RAM I do not use swap, but again do not see how many  apps I can open at once. Some say they work without swap, but I think  some is good, and others say it may boot a bit faster as it looks for  swap and has to time out on not finding any. Not sure who is right. 
I do not hibernate, even before my SSD as it booted fast enough. Of  course coming from XP with its 3 to 4 min boot anything is fast.

Well  it is for hibernating as well, no? Also, having the option for RAM  overflow could be useful. I close down programs I am not using etc too,  but sometimes when working and doing personal stuff at the same time a  lot can be open. Again, why not hibernate when dual booting? [COLOR=#ff0000]**Is  there something wrong with hibernating when dual booting or is it just a  personal preference you have to fully shut down all of the time dual  booting or not?**[/COLOR]

> **oldfred said:**
> I do not see an advantage to a small /home, if  that is what you want then I would include it inside / and maybe make /  larger. I use 25GB for / including /home but am aggressive in moving  data & data folders into my data partitions, so my /home is only 2GB  with 1.5GB for .wine. My wife uses the Windows version of Picasa in  .wine and that takes some space. I put my Firefox & Thunderbird  profiles in my shared NTFS so I have the same profile for all my  installs. It is NTFS only to share with XP, but I do not now boot  XP.

Well one possible advantage would be what I have been asking about throughout this thread and I am still trying to understand if you think it is the best option for me - [COLOR=#ff0000]**I currently have no data partition (shared or otherwise)**[/COLOR],[COLOR=#ff0000]**  if I reduce the size of the home partition (which I will keep on its  own partition for reinstalls) from ~140 to 20/30GB (I use WINE too), and the WIN8  partition from 300GB to 50/60/70GB I could create a ***SINGLE*** shared data  partition onto which I could store media ***AND*** install WIN8 \Program Files and  \Program Files (x86) -**[/COLOR] [B][COLOR=#ff0000]Please state clearly if you think this is what I should do and if you know of any reason not to do so?  

[/COLOR][/B]I  downloaded something on linux today I wanted to use later on Windows.  Although I could copy the files from my EXT4 /home partition to my WIN8  NTFS partition when I tried to use the files after booting Windows I was  told I do not have the correct permissions. I can cope with only being  able to access my Windows partition from linux and not vice versa, but I  do not want to have to mess with permissions every time I want to transfer a file.

Also, with a shared data and program files partition the space I need for media and games is there waiting for me, and I will not have to worry that the partition I want to install games or copy media on is too small or too big because another partition is too big or too small - the space is just there waiting for me on the shared partition for whatever I want to do with it.

> **oldfred said:**
> I do not know what files you see from UEFI menu, at top level you should  have Windows and ubuntu as those are the folders in the efi partition.  If using secure boot you boot Windows and that really is grub2's shim  file renamed to Windows efi file name. Normally in ubuntu should be the  grub file to boot.
[COLOR=#ff0000][B]
Would I know if I had secure boot configured?[/B][/COLOR]

> **oldfred said:**
> You  can turn off os-prober until they fix the bug in grub2. And all the  entries in 25_custom are from Boot-Repair.

# I add this line to grub configuration or turn off the execute bit on 30_os-prober
 gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executable bit
sudo chmod a-x /etc/grub.d/30_os-prober
# Then do:
sudo update-grub
Or one liner
 sudo echo GRUB_DISABLE_OS_PROBER=true >> /etc/default/grub 
sudo update-grub

   sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkup25_custom
gksudo gedit /etc/grub.d/25_custom
Then do:
sudo update-grub
[B][COLOR=#ff0000]
What will this accomplish and how will I know if it worked?[/COLOR][/B]

---

### Post by oldfred on 2013-05-10
Your screen shot and last question are the same thing. You can turn off os-prober and edit at will or delete entries in 25_custom. Just only change the menu entry in the quotes as that is what you see or delete entire boot stanza or it will not update. Each boot stanza is from menuentry line to last line }. I had an error in one of mine - missing end } for several years and never noticed a missing stanza. When grub updated to 1.99 it would not update anything until I found my typo.

I have only shared data in NTFS partitions. I do believe someone else posted a question on permissions, but NTFS does not support any Linux ownership nor permissions. You do have to set defaults when you mount with fstab. Windows 8 may do its own thing, but I do not have Windows 8 and do not plan to.

I multi-boot Ubuntu and cannot hibernate as I share swap. But some systems have issues with hibernating, both with Windows and Linux. It will not boot a lot faster, but if it works for you.

---

### Post by Dáire Fagan on 2013-05-10
Please please please answer the questions I have asked.

---

### Post by oldfred on 2013-05-10
I thought I did. 
If system boots with secure boot on then you must have it. Otherwise you have to boot Windows with secure boot, go back to UEFI and boot Ubuntu installer and use Boot-Repair with Secure boot check box and install grub2's shim and signed kernels. 
Or by looking at boot repair BootInfo, if you have shim you have the signed versions.

---

