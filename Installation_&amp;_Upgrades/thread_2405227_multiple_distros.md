---
title: "multiple distros"
date: 2018-11-03
forum: Installation &amp; Upgrades
---

### Post by oneleded on 2018-11-03
i am still some new to linux or even ubuntu. i want to install mulitable dristo's, on the 2nd HD, that is only linux. now i have lubuntu 18.04 LTS. i am prepared to wipe the drive, an will restore my firefox book marks at a later date. plus have lubuntu 18.04 lts, too reinstall. is there a sticky here or instruction for this. the internet search has been so vague when i search. i miss web crawler searching v/s popular= ranking

---

### Post by cmcanulty on 2018-11-03
An easy way would be to install virtual box and download any systems you want to install and put them all in virtual box.

---

### Post by Dennis N on 2018-11-03
> i want to install mulitable dristo's, on the 2nd HD
Easy to do:
1) make an ext4 formatted partition on the 2nd disk to be used for the new OS to be installed there.
2) boot the installer, and use the 'something else' option at the Installation Type screen. This leads you to the partitioning screen.
3) select the partition from the display, click 'change', and fill in details in the popup box. You want to choose / as the mount point.
4) Where to install boot loader (at bottom of screen): with ubuntu's installer, grub will always install to sda if this is UEFI, but on a bios system, you could opt to install grub on the 2nd disk (sdb) if you want.   
Proceed with the installation.

---

### Post by oldfred on 2018-11-03
UEFI or BIOS system?
And is first drive have an installed system? And then is it UEFI or BIOS.
Almost all hardware in last 5 years is UEFI.

If UEFI, often better to temporarily disconnect first drive. Grub only wants to install to ESP - efi system partition on sda, or first drive if newer NVMe type SSD.
If only Linux installs, you can use gpt whether UEFI or BIOS, but need a bios_grub for BIOS or ESP for UEFI.
So best to partition in advance and use Something Else.

If just testing another install the virtual install may be easier.

But if multiple booting, do you want to share data like Filefox profile in all installs? Then smaller / (root) partitions and one larger data partition (not /home) to be mounted in all of them may be better.

       [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
      [/URL]
 suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
Older /boot & swap not now required.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd) 
    [URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by yancek on 2018-11-03
What's on the internal drive?  Is it windows?  If so, which release?  Is it UEFI/GPT on the internal?  Are you going to use GPT or Legacy on the external drive?  Are you familiar with Linux naming conventions for drives/partitions (sda, sda1, sdb, sdb1, etc.).  You need to know this so you don't overwrite the internal drive.

If you are using Legacy on the external, you can choose to install Grub to the MBR of the second disk for each install or you can select to install Grub to the partition on which you are installing the OS.  Obviously, one of them will need Grub code in the MBR.  The default for all is to install to the MBR so make sure you check the device for bootloader installataion during each system install.  You will likely need to use the BIIOS to boot these systems.  Depends upon what you have on the internal drive.

If you are going to use UEFI/GPT, I believe that as stated above, the default will install your Grub boot code on the EFI partition on the internal drive.  You should be able to create an EFI partition on the external drive to use.  Never done that myself but it seems that if you are trying out or testing systems, using Legacy on the external would be simpler.

---

### Post by ajgreeny on 2018-11-03
It would be very useful to have some more info before telling you in detail what to do, so please show us the output of ```
sudo parted -l
``` in terminal.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

However, it is very possible without too much hassle to have several distros on one machine or hard disk; some time ago on a previous computer using legacy BIOS with a single HDD I had 5 different distros installed, all of which worked without a problem.

If you decide to go ahead with this we can also give you info about how to make use of all your data files currently in your Lubuntu home, without sharing the home, which can be problematical.

---

### Post by oneleded on 2018-11-03
> **yancek said:**
> What's on the internal drive?  Is it windows?  If so, which release?  Is it UEFI/GPT on the internal?  Are you going to use GPT or Legacy on the external drive?  Are you familiar with Linux naming conventions for drives/partitions (sda, sda1, sdb, sdb1, etc.).  You need to know this so you don't overwrite the internal drive.

If you are using Legacy on the external, you can choose to install Grub to the MBR of the second disk for each install or you can select to install Grub to the partition on which you are installing the OS.  Obviously, one of them will need Grub code in the MBR.  The default for all is to install to the MBR so make sure you check the device for bootloader installataion during each system install.  You will likely need to use the BIIOS to boot these systems.  Depends upon what you have on the internal drive.

If you are going to use UEFI/GPT, I believe that as stated above, the default will install your Grub boot code on the EFI partition on the internal drive.  You should be able to create an EFI partition on the external drive to use.  Never done that myself but it seems that if you are trying out or testing systems, using Legacy on the external would be simpler.
i got windows on the 1st hard drive, bios, Legacy. the 2nd hard dive is lubuntu 18.04 LTS. both  drive's are internal. grub is installed an when it boots, if i do nothing, it goes to 2nd HD. if i want the 1st windows drive, i gotta push 4 times on the choice while booting. i'm kinda sick of windows, an i got the obsolete XP on the 1st HD.. i very seldom use it, if at all. thanks for the info.. the 2nd hard drive is independent, of windows.

> **ajgreeny said:**
> It would be very useful to have some more info before telling you in detail what to do, so please show us the output of ```
sudo parted -l
``` in terminal.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

However, it is very possible without too much hassle to have several distros on one machine or hard disk; some time ago on a previous computer using legacy BIOS with a single HDD I had 5 different distros installed, all of which worked without a problem.

If you decide to go ahead with this we can also give you info about how to make use of all your data files currently in your Lubuntu home, without sharing the home, which can be problematical. 
i will have to practice the code tags, thanks for that. i got a ways to go. i want to do this on the 2nd HD dedicated to only linux. though this dell is old, it runs OK with lubuntu. it dont care much, for XP on the 1st HD. again,, much appreciation

---

### Post by oneleded on 2018-11-15
i will continue with this, the reason i havent bumped is because i still have to study some.. i do appreciate the help.

---

### Post by oneleded on 2018-12-13
[Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  120GB  120GB  primary  ntfs         boot


Model: ATA ST3250310AS (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  32.2GB  32.2GB  primary   ext4
 2      32.2GB  247GB   215GB   extended
 5      32.2GB  247GB   215GB   logical   ext4
 3      247GB   250GB   2687MB  primary   linux-swap(v1)


Error: /dev/sr1: unrecognised disk label
Model: Unknown (unknown)                                                  
Disk /dev/sr1: 2048B
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags: 
[/code]

i hope i got this code right. it seems to me, even, to me that the linux drive is not set up the way its supposed to be. maybe i should save my bookmarks, and re-install lubuntu 1804 LTS, then go from there. the 2nd drive, just linux lubuntu, is 250GB.

---

### Post by oneleded on 2018-12-16
> **oneleded said:**
> [Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  120GB  120GB  primary  ntfs         boot


Model: ATA ST3250310AS (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  32.2GB  32.2GB  primary   ext4
 2      32.2GB  247GB   215GB   extended
 5      32.2GB  247GB   215GB   logical   ext4
 3      247GB   250GB   2687MB  primary   linux-swap(v1)


Error: /dev/sr1: unrecognised disk label
Model: Unknown (unknown)                                                  
Disk /dev/sr1: 2048B
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags: 
[/code]

i hope i got this code right. it seems to me, even, to me that the linux drive is not set up the way its supposed to be. maybe i should save my bookmarks, and re-install lubuntu 1804 LTS, then go from there. the 2nd drive, just linux lubuntu, is 250GB.

Error: /dev/sr1: unrecognised disk label ,, is on the 2nd linux drive i believe. there is a small section i see when using Gparted. it may be yellow. i cant seem to remove it. i  dont know what it is.. it may have been a partitioning error on my part most likely.
merry holidays all

---

### Post by oldfred on 2018-12-16
I believe sr1 is your DVD/CD drive?

It looks like you have Windows on sda and Linux on sdb drive.

Did you use the Something Else install option and choose to have grub2 boot loader installed to the drive that is sdb?

And you want to keep a Windows boot loader in sda drive. Grub only boots working Windows and Windows that is not hibernated/fast boot on. And Windows will turn that back on with updates. Then when grub does not boot your Windows you may be able to directly boot by changing boot order in BIOS back to sda drive and may need f8 for Windows internal repair console.

But best to have Windows repair/recovery flash drive & Ubuntu live installer as repair drive for Linux.

---

### Post by oneleded on 2018-12-20
i do have windows on sda, and linux on sdb. i think also, i put grub in sdb drive. i had help here doing that here.. was a time i had to use F8, or maybe F12. now the PC starts with linux. or i can scroll down, to windows. linux being lubuntu.. lubuntu has three choices, windows only one. windows XP is the first HD. lubuntu is on the second HD.
 i might have been instructed to put grub on 2nd hard drive. if i do nothing, the pc opens in the 2nd HD, with lubuntu. the 2nd HD is only lubuntu 18.04 LTS. i like it that it boots to the 2nd hard drive, sdb. XP is so outdated. i still have info. there, i want to keep, an i am not interested to going past XP. when there is so much promise, here with ubuntu, or other versions, thereof. im sure i used the something else option i learned here to get grub to start in the 2nd HD. i like it that it does so. now my agenda is just to get some other distros on the 2nd hd, so i can check them out. thanks

---

### Post by oneleded on 2019-02-26
> **oldfred said:**
> I believe sr1 is your DVD/CD drive?

It looks like you have Windows on sda and Linux on sdb drive.

Did you use the Something Else install option and choose to have grub2 boot loader installed to the drive that is sdb?

And you want to keep a Windows boot loader in sda drive. Grub only boots working Windows and Windows that is not hibernated/fast boot on. And Windows will turn that back on with updates. Then when grub does not boot your Windows you may be able to directly boot by changing boot order in BIOS back to sda drive and may need f8 for Windows internal repair console.

But best to have Windows repair/recovery flash drive & Ubuntu live installer as repair drive for Linux.
i did use the something else option on the 2nd/sdb drive. ajgreeny showed me how to add/update grub in the thread; [old pc, two hard drives], 'installation & upgrades'. 
since windows XP is on 1st/sda drive, there is no point in updating it. it does have info on it, i want to keep. plus the scanner works there.

---

### Post by oneleded on 2019-03-11
my window's, on another drive, sda,.. is XP, and i dont plan on going, any further, with windows. i didn't like window's 7,, i think it was. XP, flipped upside down, an put in a blender. 
anyway, i got picture's of sdb, to show where i am at. 

file:///home/led/Desktop/drive%20picture/Screenshot%20from%202019-03-10%2000-52-02.png

file:///home/led/Desktop/drive%20picture/Screenshot%20from%202019-03-10%2000-57-20.png
i may need a bit of pratice doing this.

---

### Post by oldfred on 2019-03-12
You have to attach screen shots.
If you use the Forum's advanced Editor and paperclip icon it is easy to attach screenshots.
/home/led is your system which we cannot see.

---

### Post by oneleded on 2019-03-14
thanks, i should have known this. a brain fluctuation..  now i know where i messed up. i dont remember where advanced editor is. i do remember the paper clip icon, and have used it on other sites.

---

### Post by cmcanulty on 2019-03-14
The advanced option is under the reply box toward bottom right of web page

---

### Post by oneleded on 2019-03-14
> **cmcanulty said:**
> The advanced option is under the reply box toward bottom right of web page
i can go advanced, but still dont have the option, with the paper clip. most here can put in a face icon, while they write. i can only use Post icons.

---

### Post by Frogs Hair on 2019-03-14
The option should be there, but you can just start fresh in the next post.

---

### Post by oneleded on 2019-03-15
pictures of sdb; i found additional options. right in front of me, the whole time. thanks.  i think i was looking for a button.

---

### Post by oneleded on 2019-03-18
Thread #11 is related to thread #21,, i couldnt figure out what the yellow was in the 1st picture. i also couldn't reformat sdb2, or sdb5. it may be that i could delete 2 or 5, either.

---

### Post by oldfred on 2019-03-18
Little lock icons mean that partition is mounted.
You cannot change mounted partitions, so have to use a live installer (and still may need to swap off or unmount swap), so you can edit partitions.

       gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

---

### Post by oneleded on 2019-03-20
> **oldfred said:**
> Little lock icons mean that partition is mounted.
You cannot change mounted partitions, so have to use a live installer (and still may need to swap off or unmount swap), so you can edit partitions.

       gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
i did the swap off with swap file. thried to change sdb 2 and sdb5... the yellow partition in front of sdb2 an sdb5, i tried to get rid of it.. thats where i run into a problem. it had 12Mb space. i had a warning i had to reboot right away. so i did, i didnt even close off and running programs. ooop's .. 
now when i boot i get grub2 error. i'm running now because of, 16.10 lubuntu disk. least i can get online.  Maybe it was a grub2 repair error.. i dont know the command lines.
the weird thing was, it fixed my font issue. the only thing i really need to recover is my firefox bookmarks, maybe some logins, on firefox, or t-bird.
those are on the 1st HD, that is windows XP. at the moment, i cant get to the 1st hard drive. grub2 wont let me... maybe it was grub2 recovery, im thinking, still dont know the command lines.
i had a feeling, i didnt want to mess with the yellow part. i crashed windows many times, before i didnt. both 98 and xp.
i can use 16.10 or 17.04 to get online, till i fix this. a lot of things are working better, since this happened. some of my problems i had, (i did use the update online), are gone.. what a thick scull i have. school of hard knocks. thank you for your help, and the others that have got me this far. Ed  [i am an old one]

---

### Post by oldfred on 2019-03-20
16.10 and 17.04 are obsolete.
Best to use LTS long term support versions. 16.04LTS or 18.04LTS.

Forcing shutdown can corrupt file system especially if you had files open.
       Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term signal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system

---

### Post by oneleded on 2019-03-20
i know those are obsolete. but they will let me get back on line.. they are on cd, or dvd. i was running 18.04LTS, before i messed up. i think 16.10, is the one that works, that lets me get back online. that is the only reason i am using it, now.. i took a couple of snap shots, with my camera, of what ya said last. hopefully it will get me back on track.

---

### Post by oneleded on 2019-03-21
> **oldfred said:**
> 16.10 and 17.04 are obsolete.
Best to use LTS long term support versions. 16.04LTS or 18.04LTS.

Forcing shutdown can corrupt file system especially if you had files open.
       Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term signal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system
i dont ever do something simple. Soooo, when i turn on my PC, i hold Ctrl+Alt. then release, push the PrtScn, followed by the capital letter's.
i dont think you want me to wait till the grub rescue, part, is on the screen.

---

### Post by oldfred on 2019-03-21
The REISUB is when you have booted into your system and it locks up. You have to at least try that  before using power switch as then you may correct files and have to run fsck to repair file system first before trying to find actual problem.

---

### Post by oneleded on 2019-03-21
> **oneleded said:**
> i dont ever do something simple. Soooo, when i turn on my PC, i hold Ctrl+Alt. then release, push the PrtScn, followed by the capital letter's.
i dont think you want me to wait till the grub rescue, part, is on the screen.

i have to quote my self on occasion. i believe the yellow portion, in front of db5, sdb2 was grub2. i think i messed it  up pretty good.
if i disconnect my 2hd, it is all linux, would that at least get me control of 1st hd, which is only windows XP?
what is the official lubuntu site? is it lubuntu.me?
i think i got myself in a pickle, this time. it did say to backup, more than once.
i was doing OK , till i decided to delete the yellow part. Oh Well !! 
if i install lubuntu 18.04 LTS again, on 2nd HD, will it get rid of my grub2 issue?

maybe it was root instead of grub. that makes more sense, and why sdb1, malfunctioned.

---

### Post by oldfred on 2019-03-22
Links to all the Ubuntu flavors are here:
[https://www.ubuntu.com/download/flavours](https://www.ubuntu.com/download/flavours)

Normally last install's install of grub takes over boot and its os-prober finds other installs and adds it to grub menu.
If multiple installs and/or multiple drives, only use Something Else install option. And on combo box at bottom of partitioning screen choose drive (not normally partition) to install grub and the in BIOS boot from that drive. 
 The only reason to install grub to a partition is as a throw away as you have another working grub that you want to keep as default boot. And then you can update it to include your new install.

---

### Post by oneleded on 2019-03-22
> **oldfred said:**
> Links to all the Ubuntu flavors are here:
[https://www.ubuntu.com/download/flavours](https://www.ubuntu.com/download/flavours)

Normally last install's install of grub takes over boot and its os-prober finds other installs and adds it to grub menu.
If multiple installs and/or multiple drives, only use Something Else install option. And on combo box at bottom of partitioning screen choose drive (not normally partition) to install grub and the in BIOS boot from that drive. 
 The only reason to install grub to a partition is as a throw away as you have another working grub that you want to keep as default boot. And then you can update it to include your new install.

i'm farely sure, i messed up grub when i tried to reformat, the yellow part, sdb2 of sdb5. i used alt. 18.04LTS. it didnt have the option of try first. it did have the repair option. so i used it.
 for the 1st time trying this, i didnt do to awful bad. i know i made mistakes. i might have installed 18.04LTS, where sdb2, or sdb5 used to be. aint it a twister. anyway, to get to the 2ndHD,. i need a user name, and a password. i kinda remember the user name, but dont even recall putting a password down anywhere.
i did download, super grub 2, an put it on a CD-R. i got to go back to when i went  to a 2 drive system.
i can access 1stHD with windows, just not 2ndHD with lubuntu. the user name, and mostly the password, is my problem.

---

### Post by oldfred on 2019-03-22
You can always reinstall & restore from your backups. 
I have that down to under an hour. The actual install to an SSD is less than 10 min. Updating all the apps from an exported list takes a bit of time as it is a lot. And some configuration I still do manually, but a lot is scripted.

       [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges](http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges)

---

### Post by oneleded on 2019-03-23
i have now a grub2 disk. its unfortunate, i dont what the commands do. for a bit i messed up both drives. then i remembered i got the XP install disk. repair/r. i got windows back, and i'm going to re-format the second HD. what a journey. i had lubuntu, from just before 14.04 LTS. i do have some firefox bookmarks saved.
i will let ya know how it turns out.  ed

---

### Post by oneleded on 2019-03-26
> **oldfred said:**
> You can always reinstall & restore from your backups. 
I have that down to under an hour. The actual install to an SSD is less than 10 min. Updating all the apps from an exported list takes a bit of time as it is a lot. And some configuration I still do manually, but a lot is scripted.

       [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges](http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges)
As far as backups: "i'm glad you mention this. i have none."... miss use of grub2 disk, neither drive is known.
i am learning grub better, at the moment. i probably messed up the the point of entry. i cant remember the name at the moment. it's the entry point. 
never mind;;;  i think it is the root. time pause.. ..
now 3/28/19. or so i think.. . i downloaded "boot repair" from, "How to Geeks". i ran the program straight, so if i have to, i can send, results to the appropriate place. the 1st, drive is working, it's XP.   so far, my 2nd HDD, lubuntu, can't be found. i know when i did this. just not sure if if was the GRUB2, cd, or using, the cd/dvd, that had a version of 18,04 LTS, that did not have the option to try first, but did have a repair option. i got it from an alternate download. i think this was the operation that did me in. 2nd drive,, maybe the root.
i am at the point, i think i need help.

---

### Post by oneleded on 2019-03-28
> **oldfred said:**
> Little lock icons mean that partition is mounted.
You cannot change mounted partitions, so have to use a live installer (and still may need to swap off or unmount swap), so you can edit partitions.

       gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

 i went to both place's, gparted & fdisk instructions.. installing a new hard drive,, seems to be closer to the mistake i made.
window's see's the 2nd hard drive; sdb.; so doe's lubuntu 18.04LTS, on disk, or thumb drive.. yet, it still remains not found. in windows, using F-12 key, i have the option, booting the 1st., or the 2nd., HD. when i pick the 2nd., it is not found.
i used boot-repair, with my removable disk. i got windows back.. as far as sending the info. for that, it was not saved, so i cant send it. i should have sent it to the pastebin, before i shut down. since boot-repair, did fix windows, maybe i should run it from there.
.    When i use,  /Accessories /Disks, it say's sdb1 is mounted. however,  /System tools /GParted, say;s, sdb1 is not mounted. i think i lost the root, of sdb1.
Tis Betwixting.

---

### Post by oneleded on 2019-03-30
```
 ll 
```...  did it wrong. i will get back to this...next.  "sudo mkdir /media/mynewdrive" in my case, i think,, "sudo mkdir /media/sdb1" should work, in case i lost the mount point.. i might still have the mount point. i dont know for sure.
 f-disk say's every partition is MBR. i cant show picture's with this thumb drive, nor show the code from the terminal, at this moment. i got more editing to do on this post

---

### Post by oneleded on 2019-04-02
i copied this an pasted it. took me a bit. i've also done a few other things. i have a boot repair disk 17.04.., not 18.04lts. i have a grub2 disk.
i used 18.04 LTS disk,,  pushed F6, when options came up, i pushed the escape key.. next i edited a line at the bottom of the page. you backspace till you get to ghost, then you print; rescue /enable=true-- ,, .. i didn't get much done, i forgot to take a picture. now that disk dont want to work anymore. i took picture of the screen, i havent processed yet. ill get back to it.

llubuntu@lubuntu:~$ sudo parted -l
Model: ATA ST3120026AS (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  120GB  120GB  primary  ntfs         boot


Model: ATA ST3250310AS (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  32.2GB  32.2GB  primary   ext4            boot
 4      32.2GB  63.7GB  31.5GB  primary   ext4
 3      63.7GB  247GB   184GB   extended
 2      247GB   250GB   2687MB  primary   linux-swap(v1)


Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sdc: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      32.8kB  1082MB  1082MB  primary               boot, hidden


Model: Unknown (unknown)
Disk /dev/zram1: 525MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0.00B  525MB  525MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram0: 525MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0.00B  525MB  525MB  linux-swap(v1)
lubuntu@lubuntu:~$  

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

lubuntu@lubuntu:~$ sudo blkid
/dev/sda1: UUID="AE3CEE213CEDE475" TYPE="ntfs" PARTUUID="d7ead7ea-01"
/dev/sdb1: UUID="7fb2f8d8-3322-47be-85cb-fcc469726110" TYPE="ext4" PARTUUID="578d4059-01"
/dev/sdb4: LABEL="led" UUID="7deb3084-7972-4035-bc54-c594377902fe" TYPE="ext4" PARTUUID="578d4059-04"
/dev/loop0: TYPE="squashfs"
/dev/sdb2: UUID="0f7447dc-2b52-4d2c-add1-56df2372b301" TYPE="swap" PARTUUID="578d4059-02"
/dev/sdc1: UUID="2018-04-26-18-42-09-00" LABEL="Lubuntu 18.04 LTS i386" TYPE="iso9660" PARTUUID="16defdd1-01"
/dev/zram0: UUID="5cf4a6d4-d432-4c14-81fa-010c56009c00" TYPE="swap"
/dev/zram1: UUID="91aca595-58a5-4489-8bce-64776ad82523" TYPE="swap"
lubuntu@lubuntu:~$ sudo -l
Matching Defaults entries for lubuntu on lubuntu:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User lubuntu may run the following commands on lubuntu:
    (ALL : ALL) ALL
    (ALL) NOPASSWD: ALL
lubuntu@lubuntu:~$ sudo parted -l

---

### Post by oldfred on 2019-04-02
Partitioning looks normal for old BIOS/MBR system with Windows on sda & Linux on sdb.

How much RAM, does your system have? Very old systems did not have much RAM and now you need more even with Lubuntu.

---

### Post by oneleded on 2019-04-03
at the moment 2 GB ram.. got room for 2 more GB. i got some more picts. to show.
 it is a grub issue in my opinion. still a newbie, always will be, i hope.
problem didnt start, till i got into sdb4, it had a hidden partition at the front. when i tried to eliminate it, that is when my boot/grub problems started.
i thought grub2 would only be on sdb1, and windows sda.
as far as older drive's, counting down the days..
i have boot repair 17.04 on disk. is that a problem with 18.04 LTS?
i also have 2 0r 3 code numbers, that help the problem,  from boot repair, should i just send them? i am getting to the point of solving this
, i cant go much further. i shouldnt waste your time. it will solve this, but i learn better from the hard knock school.
both drives look healthy to window's XP.
 it is an interesting puzzle. i'm getting close. i dont have all the pieces. sorry to ramble so.
 where do i send the number's to?, just in case. i dont feel right, posting openly?

---

### Post by oldfred on 2019-04-03
You should always have a live installer of the current version of every system you have installed.
And with Windows a current version repair/recovery drive.

Old versions may or usually may not work as they will not be able to download necessary updates or have updated drivers.

---

### Post by oneleded on 2019-04-04
i believe you are so right.. i'm working on it at the moment. i've been thinking some, [watch out], that the yellow part of a partition i tried to delete, may have been the root sector.
that might explain why, why my sdb1 drive was not seen. i also was thinking about about saving sdb1, but reformat the rest of the drive, so that it is in order. at the moment, sdb2 is the swap partition. i started this in 2016, when i didnt have a clue. i wont say thats changed. anyway, the report says my drive is not in order. i already knew this. is it of importance?
i am going to replace the d-drive,, read only, an probably 2002 model. i cant understand why i can only use, a disk a few times, and then it quits working, unless xp, which i have to use, has, so much rust, it just wont think. if so, i do understand. some bigger thumb drive's will help, before i get into tb's. i still want to learn the bottom, an mean too.

---

### Post by oneleded on 2019-04-05
just found this;
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
fsck.ext2: Permission denied while trying to open /dev/sdb1
You must have r/w access to the filesystem or be root
lubuntu@lubuntu:~$ sudo fsck -y /dev/sdb1
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
/dev/sdb1: clean, 11/1970416 files, 167726/7869696 blocks
lubuntu@lubuntu:~$ sudo fdck -y dev/sdb4
sudo: fdck: command not found
lubuntu@lubuntu:~$ sudo fsck -y /dev/sdb4
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
/dev/sdb4: clean, 11/1921360 files, 164648/7680000 blocks
lubuntu@lubuntu:~$ sudo fsck -y /dev/sdb3
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb3
Could this be a zero-length partition?
lubuntu@lubuntu:~$ 
dont know what it means exact, but is on the right path.

i just copy from the terminal, and paste. i never could get the hang of, doing it correct.

---

### Post by oldfred on 2019-04-05
The fsck program only works on ext family of formats. Or ext4 now in most cases.

Did you try to run fsck on swap or the extended partition, as then you get that type of error.

---

### Post by oneleded on 2019-04-06
my 2nd HD is ext4. all of it.  sdb1 is the lubuntu 18.04 LTS. then i made the swap partition, sdb2. and from there the rest of the partitions.. that is why the partitions are not in order.

fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
fsck.ext2: Permission denied while trying to open /dev/sdb1
You must have r/w access to the filesystem or be root
lubuntu@lubuntu:~$ sudo fsck -y /dev/sdb1
fsck from util-linux 2.31.1

except for sdb1, i can reformat, the rest of the drive. sdb1 is the partition with the operating system on it.
the 'Permission denied" may be the problem;;    "accessories / disks / edit mount options " ,, has an on and off button. when it is off, the mount point reads,  /mnt/volume number####.
if its OK, i can show that page. i dont know if showing the volume number matters.  "You must have r/w access to the filesystem or be root"  that is where i think the problem is.. mostly the root part.
 i'll keep chipping at it. 
i have 2, http; paste. ubuntu.com ### 's  i can send from boot repair. i havent figured out yet,  how that works..

---

### Post by oldfred on 2019-04-06
Boot-Repair will automatically copy to pastebin, if Internet is working. 
You just need to post link.
 You also can copy just about anything  to pastebin site and post link, but forum accepts some data, just not the size most Summary reports from Boot-Repair are.

---

### Post by oneleded on 2019-04-06
i cant remember for sure if the internet was on. i got this;   [http://paste.ubuntu.com/p/xHXc6HtjRd/](http://paste.ubuntu.com/p/xHXc6HtjRd/)  ,,,  and, [Http://paste.ubuntu.com/p/tQjYx6KZkJ/](Http://paste.ubuntu.com/p/tQjYx6KZkJ/)   ...
i checked it, and it works. for some reason my 2nd HD, is invisible, when it comes to boot time. no doubt its something i did. is it time to give up, and reformat the whole drive? or should i keep trying. i hate to waste your time, if it cant be done. this is the line i need to concentrate on.
  fsck.ext2: Permission denied while trying to open /dev/sdb1
You must have r/w access to the filesystem or be root  ...  if i label sdb1 casper-rw,  maybe that might help.

---

### Post by oldfred on 2019-04-06
Have you tried Boot-Repair's advanced mode?
       [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    

It seems it is not seeing your install on sdb.
Never run auto fix with two drives & two installs as it wants to install same boot loader to all drives.
You have the generic Windows type boot loader in both drives.
But need to get grub installed to sdb, and then set BIOS to boot from sdb.
Install on sdb, looks like it is missing files also, may be just easier to reinstall & restore your data from your backups. Be sure to only use Something Else, install to sdb & install grub boot loader to sdb.

---

### Post by oneleded on 2019-04-06
OK i'm getting somewhere. i didn't due back-up, though i know better. for me, its probably better to reformat the 2nd HD. unplug the XP, 1st hard drive, before install, then start from scratch.
i think i am missing files, an then some. i thought i was going down this road. your help is much appreciated.
i got one more question. when i started to download 18.04.2, i was asked which devise to download boot loader to. this was with sdba, still going,1st HD,  plus 2nd, lubuntu partioned drive..
had thing's been working, and i wanted to use sdb4, should i pick sdb4, or go with sda, first drive. it would be much simpler with 1st HD unplugged. but in the 2nd, which has sdb1,sdb4, and sdb3,, i not sure if those count as a devise. they have there own drive number's so to speak..

---

### Post by oldfred on 2019-04-06
You do not install grub2 to a partition like sdb2, only to a drive like sdb or sda.
If both drives plugged in, you want to install grub to same drive as your install or it should be sdb, unless drive order changes somehow.
Sometimes plugging in a flash drive changes order. My system often sees flash drive as sda, then sda becomes sdb etc.

---

### Post by oneleded on 2019-04-06
my sdb drive is in disorder, because of the way i installed it. first sdb1, then swap, sdb2, then i partitioned some more. i will try to install grub to sdb. i understand what you are saying though.

---

### Post by oneleded on 2019-04-08
when using my usb lubuntu 18.04. it seems to have trouble with getting grub, or grub2, so i can install it.
i put slacko on a cd-rw. i might have better luck.
 i didnt format the usb, as rw. plus its fat32, which may not matter, but i think i can format it as ext4. it could function better, if it works as a drive.
the grub2 rescue disk, doesnt have an install function i can find. it cant find grub on sdb, nor install it.
i disconnected my 1st HD, windows. so now my linux drive is sda. at the moment, i am at a stop, but want to keep on trying.
1st update of my problem;;  it was suggested, i put casper-rw on the label. i did with sbd1, an sdb4. this time when i went to install 18.04.2 on sdb4, [temporary, sda4], it took. the install said it installed grub. guess i'll find out.
2nd update of my problem; i have 2nd HD back. it starts with sdb4. now to move from there.
i couldnt have done it without help from here.. thank's

just a thought, should i install grub2 now, on sba4, or wait till i hook up my 1st HD. it will be sdb4 then.??

---

### Post by oldfred on 2019-04-08
You do not install grub to a partition, just to the MBR of a drive.
So normally last install has the grub in control, but should offer to boot other installs.

From inside a working install:
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub 
    
Note that major updates to grub may reinstall it to MBR. If any other install then does that, it then becomes default boot until you reset your main working install to be default.

You can with BIOS installs change this settings which tells grub where to reinstall. If you blank it out on second installs, then only main install will remain as updateable.

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short  
    sudo grub-probe -t device /boot/grub 
   #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by oneleded on 2019-04-08
i ran this without the 1st HD connected. 

From inside a working install:
#reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo parted -l
#if it's "/dev/sdb" then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub 
only, i didnt have any errors. and i used /dev/sda in stead of sdb.. i need to plug in the 1st HD windows drive, before i can proceed, and use /dev/sdb.
i am booting to linux, with only one drive working, my linux drive. it might be a bit before i get back, been a long night. it will be soon as possible. i need both drives working, to check my progress.

---

### Post by oneleded on 2019-04-08
i connected the 1st HD windows kp. i ran some commands,
Model: ATA ST3250310AS (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  32.2GB  32.2GB  primary  ext4            boot
 4      32.2GB  63.7GB  31.5GB  primary  ext4
 2      247GB   250GB   2687MB  primary  linux-swap(v1)


ed@led:~$ sudo grub-install --rechack /dev/sdb
grub-install: unrecognized option '--rechack'
Try 'grub-install --help' or 'grub-install --usage' for more information.
ed@led:~$ sudo grub-install /dev/sdb
Installing for i386-pc platform.
Installation finished. No error reported.
ed@led:~$ sudo update grub
sudo: update: command not found
ed@led:~$ sudo update-grub
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-47-generic
Found initrd image: /boot/initrd.img-4.15.0-47-generic
Found linux image: /boot/vmlinuz-4.15.0-20-generic
Found initrd image: /boot/initrd.img-4.15.0-20-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
ed@led:~$ grub-pc/install_ devices;
bash: grub-pc/install_: No such file or directory
ed@led:~$ grub-pc/install_devices
bash: grub-pc/install_devices: No such file or directory
ed@led:~$ - grub-pc/install_devices:
-: command not found
ed@led:~$ -grub-pc/install_devices
bash: -grub-pc/install_devices: No such file or directory
ed@led:~$ sudo debconf-show grub-pc& for BIOS with grub-pc
bash: syntax error near unexpected token `with'
ed@led:~$ sudo grub-probe -t device /boot/grub
/dev/sdb4
ed@led:~$ sudo grub-install /dev/sdb
Installing for i386-pc platform.
Installation finished. No error reported.
ed@led:~$ -grub-pc/install_devices
bash: -grub-pc/install_devices: No such file or directory
ed@led:~$ - grub-pc/install_devices:
-: command not found
ed@led:~$ sudo lshw-C Disk -short
sudo: lshw-C: command not found
however i can use the F12 function to boot to xp, or sdb4, lubuntu

---

### Post by oldfred on 2019-04-08
Its not a command. You run this:
sudo debconf-show grub-pc

And it will show a lot of lines and then you look for a line like:
grub-pc/install_devices:

But not in your main working install, as you do not want to change that. You can look at it just for info.

---

### Post by oneleded on 2019-04-09
i got these lines;

  grub-pc/mixed_legacy_and_grub2: true
  grub2/device_map_regenerated:
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/chainload_from_menu.lst: true
  grub-pc/install_devices_disks_changed:
  grub-pc/partition_description:
  grub2/kfreebsd_cmdline_default: quiet splash
  grub2/update_nvram: true
  grub-pc/timeout: 10
  grub2/linux_cmdline:
  grub2/no_efi_extra_removable: false
  grub-pc/hidden_timeout: true
  grub-pc/install_devices_empty: false
  grub2/linux_cmdline_default: quiet splash
  grub-pc/disk_description:
  grub-pc/install_devices_failed: false
  grub2/kfreebsd_cmdline:
* grub-pc/install_devices: /dev/disk/by-id/ata-ST3250310AS_6RY2VVZ4                                         {2nd hard drive with lubuntu} 1st HD #is not mentioned.
  grub-pc/kopt_extracted: false
  grub-pc/postrm_purge_boot_grub: false
  grub2/unsigned_kernels:
  grub2/unsigned_kernels_title:

---

### Post by oldfred on 2019-04-09
This then is the drive that grub is installed into and on major updates will re-install into
 grub-pc/install_devices: /dev/disk/by-id/ata-ST3250310AS_6RY2VVZ4                                         
I assume you added the info showing that is the same drive as your Lubuntu install.

---

### Post by oneleded on 2019-04-10
i added the info. i was trying to make it obvious. i need to move grub to the 1st HD, so i dont have to push F-12, to chose my operating system. i tried to do it in bios, but it doesnt have the ability to do this. i turned on OS install, to see if it would make a difference. it did not, so i save and exit. my Available Physical Memory. went down to 16Mb after that, from 1.5Gb. i have spent much time, trying to figure out what was wrong. i couldnt get online because of low memory. boot repair has a low memory operating system. i tried it, and before it loaded all the way, it told me OS install caused low memory. Now i know not to turn, OS install on in bios. i probably spent 24 hr's on this. system was super-snail slow..
i need to install grub,, /dev/sda... then go from there. i got the install line wrote down, and install line is earlier in the thread also
found it #52
i said Ajgreeny helped me with grub, and he did. i cant remember if he told me to put it on 1st Hd, windows, so i didnt have to use F-12. however,
when i put grub on 1st HD, 
it give me first, the ubuntu option, sdb, 2nd HD,,
 or i could scroll down to sda/windows, the 1st HD.

---

### Post by oneleded on 2019-04-10
[sudo] password for ed: 
Installing for i386-pc platform.
Installation finished. No error reported.
ed@led:~$ sudo update-grub
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-47-generic
Found initrd image: /boot/initrd.img-4.15.0-47-generic
Found linux image: /boot/vmlinuz-4.15.0-20-generic
Found initrd image: /boot/initrd.img-4.15.0-20-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
ed@led:~$ 

OK;; this is where i am at now.
here is a bit more
ed@led:~$ sudo parted -l
Model: ATA ST3120026AS (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  120GB  120GB  primary  ntfs         boot


Model: ATA ST3250310AS (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  32.2GB  32.2GB  primary   ext4            boot
 4      32.2GB  63.7GB  31.5GB  primary   ext4
 3      63.7GB  247GB   184GB   extended
 2      247GB   250GB   2687MB  primary   linux-swap(v1)

i had the windows drive unplugged while, i did a test or something. now they are both on, 1st HD an 2nd HD,, 1 is windows sata,, 2 is linux sada.
maybe i need to mount sda, or put a /  
i think it already has a boot flag

---

### Post by oldfred on 2019-04-10
Most systems have drives in order of SATA ports.
Or sda is SATA0 or lowest numbered, and sdb is higher port.
If old PATA ports, it will depend on which connector you use or even which set of jumpers you use on drive.

---

### Post by oneleded on 2019-04-11
sda is sata0. i put grub on sda. now when the computer boot, i get the screen that list ubuntu first, and windows is at the bottom.
now im working on a mountpoint for sdb1. sdb4 mounts at filesystem root. sdb4 is also locked.

grub was acting up. i found grub2win.zip. this time i installed it using windows XP 1st disk
 seems to be working OK.

---

### Post by oneleded on 2019-04-12
this is kinda where i am at. i think sdb1 has the wrong mount point. i think i can still change it. i just noticed 1 of the picture's is a duplicate, it was supposed to be sdb4. it just showed mounted at  filesystem root.

---

### Post by oldfred on 2019-04-12
You show sdb4 mounted at / (root).
And sdb1 mounted by UUID.
I always label partitions.
And then partitions I only mount occasionally use the label & I better know what they are.

But if a regular partition you want to use, you should mount with fstab.

---

### Post by oneleded on 2019-04-14
^^^^ you have helped out a lot on this project of learning. now you have given me new questions. i will do some reading first. after i read a bit i will get back to this. much appreciated, that you have the patience, to take the time..
maybe, sdb1 should read at the mount point, /fstab , and then at sdb4 mount point the same, /fstab..

now i have to replace sdb4. i made a whopper of a mistake. i installed gimp, from snaptic. it didnt work right. my mistake. i compounded it though, using snaptic, to uncheck boxes, and go from there.  i musta unchecked 1 to many, maybe a child dependency.  when i got done, i lost the control box. (i will clean the spelling up later], i had limited function, an no way even to exit, or turn off, sdb4. i tried to correct this, with a dvd. i put the wrong one in. this one, doesnt have the, try first option. i got some dyslexia problems that get worst when i am in a hurry. LOLS. any way i stopped the install, fornunate, it was going to sdb4, instead or XP, or sdb1. i also think i may understand the purge function, better now.
i plan on saving sdb1, and reformat the rest.
do i need the swap file, if i am not using windows on this drive? i will still have many partition's.

---

### Post by oldfred on 2019-04-14
Ubuntu now uses a swap file.
But if you have a swap partition it will use it.

---

### Post by oneleded on 2019-04-15
at the moment windows xp/ sda is on sata0, and is still working.
i/m working on linux/sdb, sata1. once i get linux working, correct, i should make  it the first sata drive-0., [sda], put grub on it, 
and windows, will be sata1, sdb drive., or, i got to change the jumpers, in back of the drive.

when you changed the jumpers with PATA drives, didnt it reduce the volume of the drive?
i am using sata drives, though.

those picture's have changed, post #62. when i made the mistake in post#64, it changed things.

---

### Post by oldfred on 2019-04-15
The nice thing about SATA drives is no jumpers, I really really hated those tiny little jumper pins.

Best to keep each drive separate or always have grub on Ubuntu drive and BIOS set to boot Ubuntu drive. 
Then it really does not matter if sda or sdb.

---

### Post by oneleded on 2019-04-16
those little tiny jumper pins were a pain, to get to, an then to drop one.  though i cant change the sata order with the bios, i can change the orange plugs on the motherboard, or the drive's, depending on what is easier.
i hope ya can see these pictures. while i was fumbling around, i changed the way, GParted sees sdb HDD, an the way, Disks sees sdb HDD.
i have to go through this tread, an recopy the command lines.
for the moment;; i will look up how to leave a small root file., mount with fstab.
in the one picture, i show mount options. is is off. it shows Mount Point. can i change it there, or should i search some more? i would rather search some, before i give up.
about those jumpers; there are probably some still on the basement floor, somewhere. i made sure i got them out of old drives, in case i need one. Ha Ha
at the moment i cant boot to sdb, because of my mistakes. i have 1 question, that pertanes to sdb.. on sdb1 i have a boot flag. i dont know if i need it, i may have put it there myself an believe so. my question is, 
Do i need boot flags, on partitions, or drives, or both??

---

### Post by oldfred on 2019-04-16
Boot flag is used by Windows & syslinux boot loaders.
Grub does not use boot flag.
But a few motherboards (Intel for sure) have BIOS that expects a boot flag (assumes Windows?), so we normally suggest a boot flag on a primary partition.

Disks is a gui way to add a data partition to fstab. But it does not always use best parameters. 
Better just to use template. But then you also have to create a mount point and maybe give yourself ownership & permissions.
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

---

### Post by oneleded on 2019-04-16
let me catch up a bit, reread posts, and i will. sunny outside. i have to do this first. after i read a bit [i.e. study], maybe i will learn to make root small, in regards to drive, and partitions.
lubuntu,,. nice puzzle.

---

### Post by oneleded on 2019-04-18
> **cmcanulty said:**
> An easy way would be to install virtual box and download any systems you want to install and put them all in virtual box.
just to let ya know, i did pay attention to this.
on on the other side of the coin, i am going to the start of this thread, and reread it, more than a few times..

---

### Post by oneleded on 2019-04-18
> **oldfred said:**
> You have to attach screen shots.
If you use the Forum's advanced Editor and paperclip icon it is easy to attach screenshots.
/home/led is your system which we cannot see.
i went back to the beginning. /home/led; is probably the 1st thing i should have concentrated on.

---

### Post by oneleded on 2019-04-19
> **oldfred said:**
> Ubuntu now uses a swap file.
But if you have a swap partition it will use it.
since i will be using other dristro's, on the linux drive, shouldnt i keep the swap partition? just in case.
should i just swapoff or un-mount swap, whether i need to or not, when editing with a live installer?

---

### Post by oldfred on 2019-04-19
Other distros may want swap.
But you cannot hibernate nor encrypt an install and use same swap as another system will overwrite what is saved. But if not do either, then you can share a swap partition. Swap file is inside Ubuntu so would not be shared.

---

### Post by oneleded on 2019-04-20
^^^^ thanks; that is what i thought, but wanted to confirm it. ( info with swap)
getting back,, "/home/led" on sdb1 is beyond my knowledge. i've read, and reread mount/umount options from many different sources.
sdb4, i cant repair, because it is mounted. i can use umount; then try. i might as well. 
in the end i have to re-establish  "/home/led" for sdb1,, an, "/root" for sdb4..
then there is the end-game option of just starting over. 
the easy way out, so to speak. that would free up your time, and mine.
i dont mind spending my time. not the same with yours.
i just might have messed up sdb, and its partitions, where they cant be fixed.
do i still got a shot?
i forgot to add;; i got the generic grub2 back on 1st XP drive, sda. when, booting,  i choose the ubuntu/lubuntu option, i get a black screen, with white writing. i got past name, an password. its for sdb4 i think. the repair, wont work, because the sdb4 partition is mounted, . it does not show up on the resent pictures, but, it seems, it still is mounted, and not so accessible.. i have to go back an tell ya the post #number, that shows it. got the star, an other sign's.

---

### Post by oneleded on 2019-04-21
i wanted to copy and paste this before i lose it. i deleted everything on the sdb drive, except, sdb1. that was where my problem began. my next move is to reestablish, /home/led.. i checked several sites over the past few days, an i might be onto something.. .. 
lubuntu@lubuntu:~$ etc/fstab
bash: etc/fstab: No such file or directory
lubuntu@lubuntu:~$ /etc/fstab
bash: /etc/fstab: Permission denied
lubuntu@lubuntu:~$ sudo /etc/fstab
sudo: /etc/fstab: command not found
lubuntu@lubuntu:~$ sudo umount /dev/sdb1
umount: /dev/sdb1: not mounted.
lubuntu@lubuntu:~$ umount /dev/sdb
umount: /dev/sdb: not mounted.
lubuntu@lubuntu:~$ fsck -A /dev/sdb
fsck from util-linux 2.31.1
lubuntu@lubuntu:~$ fsck -y /dev/sdb
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
fsck.ext2: Permission denied while trying to open /dev/sdb
You must have r/w access to the filesystem or be root
lubuntu@lubuntu:~$ sudo fsck -y /dev/sdb
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

Found a dos partition table in /dev/sdb
lubuntu@lubuntu:~$ sudo fsck -y /dev/sdb1
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
/home/led: clean, 11/1970416 files, 167726/7869696 blocks
lubuntu@lubuntu:~$ sudo fsck -r /dev/sdb1
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
/home/led: clean, 11/1970416 files, 167726/7869696 blocks
/dev/sdb1: status 0, rss 2848, real 0.140497, user 0.046076, sys 0.004188
lubuntu@lubuntu:~$ # touch /forcefsck
lubuntu@lubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdb1
                                                                               
          11 inodes used (0.00%, out of 1970416)
           0 non-contiguous files (0.0%)
           0 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 3
      167726 blocks used (2.13%, out of 7869696)
           0 bad blocks
           1 large file

           0 regular files
           2 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------
           2 files
lubuntu@lubuntu:~$ sudo e2fsck -f -y -v /dev/sdb1
e2fsck 1.44.1 (24-Mar-2018)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

          11 inodes used (0.00%, out of 1970416)
           0 non-contiguous files (0.0%)
           0 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 3
      167726 blocks used (2.13%, out of 7869696)
           0 bad blocks
           1 large file

           0 regular files
           2 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------
           2 files
lubuntu@lubuntu:~$ ls -al /media/
total 0
drwxr-xr-x 1 root root  60 Apr 21 17:47 .
drwxr-xr-x 1 root root 260 Apr 21 17:47 ..
lrwxrwxrwx 1 root root   6 Apr 21 17:47 cdrom -> /cdrom
lubuntu@lubuntu:~$ ls -al /media/aelm/
ls: cannot access '/media/aelm/': No such file or directory
lubuntu@lubuntu:~$

---

### Post by oneleded on 2019-04-21
i thought i was careful not to involve 1st. hd sda windows XP. i. maybe was not careful enough. i might have upset grub, by what i was doing. it dont like change. happy easter anyway.
i know to use the generic windows, grub2., for sda/xp.. ..
i did remove fast boot from xp or bio's. it makes a difference. i dont have to race to get to F-lock key, to use the F12 key. it dont slow loading down all that much anyway., or even speed it up..

---

### Post by oldfred on 2019-04-21
You only run fsck on a partition like sdb1, not on a drive like sdb or sda.
That is why you has so many errors at beginning.

---

### Post by oneleded on 2019-04-23
while i was running sudo command's; i ran something like this; sudo umount -a etc.. i think -a included XP on sda1.  any way, with grub or repair disk, i got windows xp back...
i only had the XP drive in. the yellow/orange cord broke to one of the sata drives, i figured i needed it more with XP..  i repaired the cord, though my iso sees sdb, grub doesnt.
"grub legacy".
i think i need to update grub, from my live 18.04 disk. 1st.
once sdb is seen, then,,, 
i copied a few commands that might get back,  /home/led..  =sdb1
they are on my camera, an without XP working, i couldnt print them, or copy them here.
 sometimes i dream or think, mkdir. maybe a few others. must be making some progress. thanks,  ed

---

### Post by oneleded on 2019-04-25
just a small question. is RAID, important to me? and do i need it?.. i dont think so. 
  y/n
got one more question? when formatting to ext4, is ext4 64-bit?
 y/n . i read a post, dont mean it's true. and if it is, as long as it works, i dont care.

---

### Post by oldfred on 2019-04-25
ext4 is used on both 64 & 32 bit systems.

RAID is not backup but for uptime.
       Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by oneleded on 2019-04-25
i dont what RAID is, so i never used it. i found, code ll,  in an earlier post, around #34. i must have used, sudo ll, at the time, so it didnt work.  this time i got it.
 i ran a mount command trying to get it to mount to, /home/led. that didnt work. i cant show the command, i used, i forgot to copy it. is said, no such mount point.
before i installed grub legacy to sda drive. grub did see lubuntu, though i couldnt boot to sdb1. mount: /dir: No such file or directory.  i ran this today in terminal also;
lubuntu@lubuntu:~$ sudo mkdir /mnt/sdb
lubuntu@lubuntu:~$ sudo mount /dev/sdb /mnt/sdb
mount: /mnt/sdb: /dev/sdb already mounted or mount point busy.
lubuntu@lubuntu:~$ # mount -t ext4 /dev/sdb /mnt/ext4
lubuntu@lubuntu:~$ ll
total 28
drwxr-xr-x 16 lubuntu lubuntu  500 Apr 25 21:16 ./
drwxr-xr-x  1 root    root      60 Apr 25 21:10 ../
-rw-------  1 lubuntu lubuntu   52 Apr 25 21:12 .Xauthority
-rw-------  1 lubuntu lubuntu  139 Apr 25 22:29 .bash_history
-rw-r--r--  1 lubuntu lubuntu  220 Apr 25 21:10 .bash_logout
-rw-r--r--  1 lubuntu lubuntu 3771 Apr 25 21:10 .bashrc
drwx------  7 lubuntu lubuntu  160 Apr 25 21:19 .cache/
drwxr-xr-x 15 lubuntu lubuntu  380 Apr 25 21:14 .config/
drwx------  3 lubuntu lubuntu   60 Apr 25 21:12 .gnupg/
drwx------  2 lubuntu lubuntu   40 Apr 25 21:10 .gvfs/
drwx------  3 lubuntu lubuntu   60 Apr 25 21:10 .local/
drwx------  5 lubuntu lubuntu  100 Apr 25 21:17 .mozilla/
-rw-r--r--  1 lubuntu lubuntu  807 Apr 25 21:10 .profile
-rw-r--r--  1 lubuntu lubuntu    0 Apr 25 21:15 .sudo_as_admin_successful
-rw-r--r--  1 lubuntu lubuntu   14 Feb 12  2018 .xscreensaver
-rw-------  1 lubuntu lubuntu 2399 Apr 25 21:12 .xsession-errors
drwxr-xr-x  2 lubuntu lubuntu   60 Apr 25 21:10 Desktop/
drwxr-xr-x  2 lubuntu lubuntu   40 Apr 25 21:13 Documents/
drwxr-xr-x  2 lubuntu lubuntu   40 Apr 25 21:13 Downloads/
drwxr-xr-x  2 lubuntu lubuntu   40 Apr 25 21:13 Music/
drwxr-xr-x  2 lubuntu lubuntu   40 Apr 25 21:13 Pictures/
drwxr-xr-x  2 lubuntu lubuntu   40 Apr 25 21:13 Public/
drwxr-xr-x  2 lubuntu lubuntu   40 Apr 25 21:13 Templates/
drwxr-xr-x  2 lubuntu lubuntu   40 Apr 25 21:13 Videos/
-rw-rw-r--  1 lubuntu lubuntu    0 Apr 25 21:16 ls
Not seeing install, not finding, /home/led and now, grub not seeing lubuntu, about sums it up..
maybe time for fresh install. ??

---

### Post by oldfred on 2019-04-25
You ran the ll command on the live installer, named lubuntu@lubuntu?
You mount partitions like sdb1 not drives like sdb.

---

### Post by oneleded on 2019-04-26
i ran, ll, comand using installer. 
lubuntu@lubuntu:~$ ll /dev/sdb1   {I ran this using installer}what i paste now is also using the installer
brw-rw---- 1 root disk 8, 17 Apr 26 19:15 /dev/sdb1

lubuntu@lubuntu:~$ findmnt /
TARGET SOURCE FSTYPE  OPTIONS
/      /cow   overlay rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/u
lubuntu@lubuntu:~$ find mnt /cow
find: &#8216;mnt&#8217;: No such file or directory
find: &#8216;/cow&#8217;: No such file or directory
lubuntu@lubuntu:~$ findmnt /cow
TARGET SOURCE FSTYPE  OPTIONS
/      /cow   overlay rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=
lubuntu@lubuntu:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
udev             1007612       0   1007612   0% /dev
tmpfs             205136    1120    204016   1% /run
/dev/sr0         1056640 1056640         0 100% /cdrom
/dev/loop0       1000960 1000960         0 100% /rofs
/cow             1025676   87352    938324   9% /
tmpfs            1025676   33576    992100   4% /dev/shm
tmpfs               5120       4      5116   1% /run/lock
tmpfs            1025676       0   1025676   0% /sys/fs/cgroup
tmpfs            1025676     520   1025156   1% /tmp
tmpfs             205132       8    205124   1% /run/user/999
lubuntu@lubuntu:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
fd0      2:0    1     4K  0 disk 
loop0    7:0    0 977.5M  1 loop /rofs
sda      8:0    0 111.8G  0 disk 
&#9492;&#9472;sda1   8:1    0 111.8G  0 part 
sdb      8:16   0 232.8G  0 disk 
&#9500;&#9472;sdb1   8:17   0    30G  0 part 
&#9500;&#9472;sdb2   8:18   0     1K  0 part 
&#9492;&#9472;sdb3   8:19   0   5.9G  0 part [SWAP]
sr0     11:0    1     1G  0 rom  /cdrom
sr1     11:1    1  1024M  0 rom  
zram0  252:0    0 500.8M  0 disk [SWAP]
zram1  252:1    0 500.8M  0 disk [SWAP]

lubuntu@lubuntu:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1007612k,nr_inodes=209036,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=205136k,mode=755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=25,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=14253)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=205132k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)

lubuntu@lubuntu:~$ df /dev/sdb1
Filesystem     1K-blocks  Used Available Use% Mounted on
udev             1007612     0   1007612   0% /dev
lubuntu@lubuntu:~$ mount /dev/sdb1
mount: /dev/sdb1: can't find in /etc/fstab.
lubuntu@lubuntu:~$ lsblk /dev/sdb1
NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
sdb1   8:17   0  30G  0 part 
lubuntu@lubuntu:~$ ll /dev/sdb1
brw-rw---- 1 root disk 8, 17 Apr 26 19:15 /dev/sdb1   { ,dev/sdb1, was in yellow}most the time the writing is in white..

i going to mount to; /dev/sdb1/
Should it include/ ; /home/led
i am not sure of my original mountpoint ?? ??

---

### Post by oneleded on 2019-04-26
when i started with 14,04 lts. i put it on sdb, 2nd hd ..  sdb1 i guess in the long run,i have upgraded since then. what was  the mountpoint with that install?, or the name of mount point with that install? i.e., i didnt make that mountpoint, it was with the install. that is what i am looking for..
in the meantime, i want to get into sdb1. i just may not be able too. maybe no one can. if there is a way, i will try.  
tell me i am on the right path.
 its easy to do a fresh install,  to get back where you were, not so much.. i dont mind the hard road if i can do it. i end up taking the hard road by nature..
hope, i didnt sound to pathetic. i still want to get to lubuntu on sdb1. i think i still can. and willing to do so.

---

### Post by oldfred on 2019-04-26
If you just install / will be mounted to the partition you install into.
This shows where / is mounted (from your install, not live installer).

cat /etc/fstab


Mine shows this, the # is a comment and if you edit it the mount could have changed, but UUID will be that partition

[cpde]# / was on /dev/sda4 during installation
UUID=c29fc361-ea05-420b-b919-850aeef65dd4 /               ext4    errors=remount-ro 0       1
[/code]

To confirm which partition is which UUID.
lsblk -f

---

### Post by oneleded on 2019-04-27
this is what i am starting with, so to speak;; no reply needed, till i ask.. it probably wont be till later, tonight, or tomorrow.

lubuntu@lubuntu:~$ cat /etc/fstab
overlay / overlay rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

lubuntu@lubuntu:~$ lsblk -f 
NAME   FSTYPE   LABEL                  UUID                                 MOUNTPOINT
fd0                                                                         
loop0  squashfs                                                             /rofs
sda                                                                         
&#9492;&#9472;sda1 ntfs                            AE3CEE213CEDE475                     
sdb                                                                         
&#9500;&#9472;sdb1 ext4     /home/led              7fb2f8d8-3322-47be-85cb-fcc469726110 
&#9500;&#9472;sdb2                                                                      
&#9492;&#9472;sdb3 swap     linux-swap             face7188-69d1-4674-beb9-ecefbec2b119 [SWAP]
sr0    iso9660  Lubuntu 18.04 LTS i386 2018-04-26-18-42-09-00               /cdrom
sr1                                                                         
zram0                                                                       [SWAP]
zram1                                                                       [SWAP]
l

sdb                                                                         
&#9500;&#9472;sdb1 ext4         /home/led                  7fb2f8d8-3322-47be-85cb-fcc469726110  <--{this line looks different in the terminal} A space between, ext4, and, /home/led, then again, a space between, /home/led, to, 7fb2f8d8etc.

---

### Post by oldfred on 2019-04-27
The fstab in lubuntu@lubuntu is the live installer, it will not reflect your install.

If you want /home in a separate partition you have to have two partitions, one for / and one for /home.
Or both can be in one partition but it would be mounted at / and /home then is just a folder inside /.

---

### Post by oneleded on 2019-04-27
i have seen so many command's for mount, and mkdir since this thread started, i am at a loss. so many different site's, so many different instructions.
will this work, as a start; sudo mount /dev/sdb1 /mnt 
some place's say to start with mkdir first, then mount. more often then not, they talk about windows, in one form or fashion, instead of, just a ubuntu drive. sdb in my case. sdb1 is my 1st., partition. i still want to save it, though i can just re-install.
/dev/sdb1: UUID="7fb2f8d8-3322-47be-85cb-fcc469726110" TYPE="ext4" PARTUUID="578d4059-01"
is still the number of sdb1.
/home/led is a place i think i might need.. i dont know that i do.. i did run across, /home/lubuntu, somewhere in my search this evening.
this also is in my scrambled notes, from weeks ago;; root@lubuntu: /home/lubuntu#
i dont remember it, i did write it in my notes.
just a few commands ran in the right way, will tell me, to keep sdb1, or throw it away, so to speak.
i've had sdb1 since 14.04LTS. i upgraded it, and once i down graded it, then upgraded it, and have upgraded it some more. the last upgrade was 18.04.2 i think.. it was still running, till i broke it.
tis a good run...
i read i might be able to do an install and still keep my files. i might have done this before, i dont know... as i read what i write, i aint quite sure, i did all the things i said. strokes will do that to ya. perhaps i still had to redo the bookmarks, an programs i had, on the last install. i know i mostly just upgraded. it will come back to me.
i got it, from 14.04lts, i couldnt get a 16.04lts disk to work. i got a 17.04 disk to work, then i upgraded to last, lts version, which was 16.04lts. from there i only upgraded manually, from download new upgrade's, lts only. thats how i got to  18.04.2 lts. till i messed up, i didnt have an 18.04.2 live disk. didnt need one.
didnt mean to ramble on so. it does explain, where i was at when i messed up, which is why this thread started.
its still important to me, and might help others. its easy to give up. not so much to correct, an go on.

---

### Post by oldfred on 2019-04-28
I thought you just wanted to install?
Not mount  an old install & try to recover data.
Better to plan good back ups, then any mistakes are not the end of the world.

---

### Post by oneleded on 2019-04-28
i can just install. its faster. the old drive may be corrupt anyway. sdb1

---

### Post by oneleded on 2019-04-29
over my mistakes, i loss excess to /sdb/hdd. i still had it 2 weeks ago. now i dont.. i cant do an install with distro on dvd. this is what i tried some today.
lubuntu@lubuntu:~$ cat /mnt/looksee etc/fstab
cat: /mnt/looksee: No such file or directory
cat: etc/fstab: No such file or directory
lubuntu@lubuntu:~$ cat /mnt/looksee /etc/fstab
cat: /mnt/looksee: No such file or directory
overlay / overlay rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
lubuntu@lubuntu:~$ sudo /mnt/looksee/ /etc/fstab
sudo: /mnt/looksee/: command not found
lubuntu@lubuntu:~$ sudo umount sdb
umount: sdb: no mount point specified.
lubuntu@lubuntu:~$ sudo umount /dev/sdb/
umount: /dev/sdb/: not mounted.
lubuntu@lubuntu:~$ sudo umount /dev/sdb1/
umount: /dev/sdb1/: not mounted.
lubuntu@lubuntu:~$ sudo umoumt /
sudo: umoumt: command not found
lubuntu@lubuntu:~$ sudo umount /dev/sdb4/
umount: /dev/sdb4/: no mount point specified.
lubuntu@lubuntu:~$ sudo umount lubuntu@led
umount: lubuntu@led: no mount point specified.
lubuntu@lubuntu:~$ sudo umount dev/sdb/ lubuntu@lad
umount: dev/sdb/: no mount point specified.
umount: lubuntu@lad: no mount point specified.
lubuntu@lubuntu:~$ sudo umount /dev/sdb/ /dev/sdb1/ /lubuntu@led/
umount: /dev/sdb/: not mounted.
umount: /dev/sdb1/: not mounted.
umount: /lubuntu@led/: no mount point specified.
lubuntu@lubuntu:~$ sudo -l /mnt/backupd/
sudo: /mnt/backupd/: command not found
lubuntu@lubuntu:~$ sudo umount -l /mnt/backups/
umount: /mnt/backups/: no mount point specified.
lubuntu@lubuntu:~$ df -k
Filesystem     1K-blocks    Used Available Use% Mounted on
udev             1007580       0   1007580   0% /dev
tmpfs             205132    1124    204008   1% /run
/dev/sr0         1056640 1056640         0 100% /cdrom
/dev/loop0       1000960 1000960         0 100% /rofs
/cow             1025644  106712    918932  11% /
tmpfs            1025644    9012   1016632   1% /dev/shm
tmpfs               5120       8      5112   1% /run/lock
tmpfs            1025644       0   1025644   0% /sys/fs/cgroup
tmpfs            1025644     520   1025124   1% /tmp
tmpfs             205128      12    205116   1% /run/user/999
lubuntu@lubuntu:~$ 
in order to do anything, i need grub and a mount point. i got some pictures to show also. just a for-warning. i have to snap some shots, get them ready in XP, copy an post here. till i post the picture shot's, ya cant see sdb hdd, the way i set it up this time. sdb1 will still be there.
i got a lot of drive, sdb, to work with. perhaps /sdb/hdd/ ???

---

### Post by oldfred on 2019-04-29
I do not understand why you need grub & a mount point.
Just do a full install from your live installer to sdb using Something Else and choose to install grub to sdb drive.

---

### Post by oneleded on 2019-05-01
i for one, do not understand neither. i didnt even know about grub when i 1st had lubuntu, on sdb 2nd., hdd.
 i must have wrote too many things using sudo.. algreeny showed me grub, and things were working great, till i stuck my thumb in the pie, so to speak. [i hope this is tame enough].. things were going great, till they weren't.
my focus is just on getting 2nd, hdd drive back. it shows up, but i cant access it.
i lost the thumb drive for a while, i managed to get it back, with time. maybe i need to just reformat the 2nd hard drive, an start over.
 one picture is missing, i dont know if its the one that says where to install the boot loader. it suggest sda.
once i get back sdb/hdd, i'll be home free.
much thanks for going this far with me.  ed

---

### Post by oldfred on 2019-05-01
As your third screen shows, choose a partition, if you do not have any data to save set at ext4, check format & choose it as / (root). If you are using second ext4 partition choose it, if you have data, DO NOT check format, use as ext4 and use as /home.
Then in combo box at bottom where it says sda, change to drive that is sdb.

---

### Post by oneleded on 2019-05-01
up, until about week or so ago, grub still could see sdb hdd. now it cant. i dont know what i did, i do know i did it.
i have to establish a way to get back into sdb/hdd. i tried, with g-parted, and disks, but cannot do,  ""set at ext4, check format & choose it as / (root)"",  the selections are not there. i did find this command on the net,,
 $ sudo tune2fs -L ROOT /dev/sda1   $ sudo e2label /dev/sda1 ROOT ,,,, it reads sda, but changing it to sdb is easy enough.
searching online, with a search engine, that list the favorite reply's, instead of what i need, is difficult at best, for me. i did better before google, an those other search engines, that work the same way now.
i think i will have the use the terminal, to get thing's right.
 i reformatted sdb1,as ext4. i still didnt get the option to set sdb1 as root. i tried to install, lubuntu 18.04.02 distro., it wont install to sdb1. i will try it again so, i can copy an paste, what it say's...
i have had problems with, mdkir command. its not recognized or something, along with, /etc/fstab.
when using something else, it always gets to the place;;
no root system is defined
please correct this from partitioning menu
i try to do this, but cant seem to somehow.. its like a broken record.
except where the drive sdb is partitioned, its blank. if i could get it back to the beginning, maybe that might help.
when i installed the dristo, i didnt know about mounting, or mountpoints.. i didnt even know about linux, or, lubuntu. [i did know of linux]

---

### Post by oldfred on 2019-05-01
Are you clicking on change on the sdb1 partition?
Are you clicking on the combo box at bottom of partitioning screen as shown in your third screen? And then change to sdb drive.That then installs grub to MBR of sdb. You do not otherwise see grub.

---

### Post by oneleded on 2019-05-02
i dont see grub, when trying to install lubuntu, from iso. i havent clicked on {change}, as yet. picture 4 show's as far as i can get, before i have to quit.

no root system is defined
please correct this from partitioning menu

i cant seem to correct this, from partitioning menu..
sdb is partitioned.. none of the partitions have any information on them. that i am aware of. all partitions should be ext4.

maybe if i click on change,  if i can find it, i can do root system.
i know its very confusing to read what i write, its worst when i say it. you have a lot of patience.

i clicked on change.. i got pictures. i also installed lubuntu 18.04.2LTS to sdb1. when i do reset, i should be back, more or less where i was. if this works, i wont have to pester ya , for a while. we'll both be happy. thumb's up

---

### Post by oneleded on 2019-05-03
this afternoon, i used Boot Repair again. this time, i got deeper in advance options. i checked every thing i thought i could get away with. that included purge grub. i didnt push anything that had to do with, windows, or legacy. the 1st hdd, windows was not hooked up anyway. i did not try, to fix MBR. then i rebooted, with Boot Repair again.
 i used advance options again. this time i only checked a few things. i checked fix grub again.
 after it was finished, i can boot into lubuntu again. at the moment, its on sda, till i plug windows drive in..  then lubuntu will be back on sdb1. i reformatted sdb1, a week ago perhaps, +/-,  a day or two, still couldnt get on the 2nd., hard drive. at least now, i can..
now;;;   plug in 1st., hdd, and see how grub works..
update;; i think i will remove grub legacy form windows. maybe purge it... grub legacy, is not what was there before any way. i think i only had grub2.. first i will an try to update grub, from sdb1.. 
boot repair, put a flag on sdb1, it also put a nose, [for lack of a description], on sdb.  09:47pm

---

### Post by oneleded on 2019-05-04
December 1st, 2016,,  ajgreeny
Code:  sudo update-grub,.  grep "menuentry " /boot/grub/grub.cfg | cut -c 1-82,...
that was a while back. but sum, i remember it. i didnt have grub back then. i had 2 HDD's, an had to use, F Lock, to get the drive i wanted to boot.
i cant remember if i was using F12,or F10.. after installing grub, ubuntu, was 1st, in line, window's last... just the way i wanted.
i think i will purge grub from windows/grub legacy.. then update grub, 2nd HDD, lubuntu. then get back to "multiple distros".. as i intended.
i think i got the 2nd. linux drive set up, as i want. maybe not as i need.
i'm still guessing at this, some also... if not more

---

### Post by oldfred on 2019-05-04
If you do not have Windows drive plugged in, or not seen by grub2's os-prober, you do not get grub menu.
Grub sees only one install, so default boots that one install.
To then get grub menu, you have to hold shift key from BIOS logo until menu appears.

---

### Post by oneleded on 2019-05-06
i got everything back, except my original lubuntu install. i Did mess that up, and then some. now to add some distro's, to play around with. maybe use, virtual drive's.
i have to show a camera shot of sdb, the way it is now. ,, maybe even re-title the thread, sum,  because of the past weeks. sure needed your help though.. i got much more to add to this.
when i installed grub2, or grub, back to 2nd. HDD, using "boot repair",, it made a difference, this time,  i went into advanced settings. it made a huge difference.  i have to admit, i didnt exactly know what i was doing. 
never the less, i am back, so to speak.

---

### Post by 1clue on 2019-05-06
I know you've gone way past the decision point on this project, but I'm going to put my 2 cents in anyway:

You gain almost nothing by installing dual boot.

Dual boot means that at any time, half the information on your disks is unusable. Yes you can get at data if your current host operating system can read the partitions of the non-active operating system, but updates and settings are all lagging. And a shared data directory when you have 2 significantly different versions of the same app (one on each distro) will lead to despair. Moreover you need to partition for each extra operating system. If you want to suspend-to-disk then you need a separate swap partition for each OS as well, which must be at least the size of RAM.

By using a virtual machine for each distro you want to try, you have simultaneous access to everything on your disks. You can fire up your host (bare metal) operating system, then fire up a VM for whatever other distro you want to try. Nothing is corrupted and you get the best of both worlds. Suspend to disk is not really necessary since the VM software will handle all that for you.

By going to 3 distros, or 4 or 5 or 20, the comments I made above are likewise scaled for better or worse. The multi-boot setup has a smaller and smaller fraction of your disk, and the VMs still have access to whatever you want, simultaneously.

You may want to try it this way the next time around.

---

### Post by oneleded on 2019-05-07
i have to reread this a couple of times,maybe, before i understand what you are saying. i got windows on 1st. hdd, an linux on 2nd hdd.. i guess that qualifies as duel boot. on the 2nd hdd.... 2nd. hdd will work better if i use VM, when installing other distro's? i'm still kinda new at this.
throw your 2 cent's in anytime ya feel like..  im still on this 1st. time around.

---

### Post by oneleded on 2019-05-07
> **oldfred said:**
> If you do not have Windows drive plugged in, or not seen by grub2's os-prober, you do not get grub menu.
Grub sees only one install, so default boots that one install.
To then get grub menu, you have to hold shift key from BIOS logo until menu appears.
i am back to where i was, weeks ago. when PC boots, i can push enter, an it boots to lubuntu, or, i can push enter 4 times, and i can boot into windows. windows is at the bottom of the list again, where it belongs.
i still have to show some screen shot's of sdb drive the way it is set up now. before i can proceed. the 1st. distro, i want to try, is slacko.. i want to put it on sdb5. i still can use VM, if necessary, perhaps.
pictures, of drive sdb, forthcoming.

---

### Post by oldfred on 2019-05-07
Use of a VM as 1clue suggests is an alternative if you have newer hardware with enough RAM to share two systems running at once.

I think you mentioned this is an older system, plus it has XP which is also older and really should not be used anymore as it is not supported by Microsoft anymore.
So your system may not support VM type install, or may not support it well.

---

### Post by oneleded on 2019-05-07
> **oneleded said:**
> i am back to where i was, weeks ago. when PC boots, i can push enter, an it boots to lubuntu, or, i can push enter 4 times, and i can boot into windows. windows is at the bottom of the list again, where it belongs.
i still have to show some screen shot's of sdb drive the way it is set up now. before i can proceed. the 1st. distro, i want to try, is slacko.. i want to put it on sdb5. i still can use VM, if necessary, perhaps.
pictures, of drive sdb, forthcoming.
i hope this picture is here.//   it is, but i can get a better picture tomorrow.

---

### Post by oneleded on 2019-05-08
i only had to use XP, because i messed up the 2nd. HD, with lubuntu. anyway, if i am on 1st., xp drive, the 2nd. lubu drive is taking up resources, or vice-versa, on 2nd. ,hd, an the 1st. XP drive is taking up resourses???
 the 1st., hd XP drive is near %50 full.  so i put lubuntu on 2nd., hd. as far as duel boot,, i'm using two sata drives, not 1 sata drive. if,, you use one drive with two operating systems, its duel boot?,, or if you run two hdd's, one operating system each, its also duel boot?? i should think, with lubuntu only on 2nd HDD, lubuntu should support, VM, and i only would have to worry about bio's.. <last word may be spelled wrong..

---

### Post by oneleded on 2019-05-09
> **oneleded said:**
> i only had to use XP, because i messed up the 2nd. HD, with lubuntu. anyway, if i am on 1st., xp drive, the 2nd. lubu drive is taking up resources, or vice-versa, on 2nd. ,hd, an the 1st. XP drive is taking up resourses???
 the 1st., hd XP drive is near %50 full.  so i put lubuntu on 2nd., hd. as far as duel boot,, i'm using two sata drives, not 1 sata drive. if,, you use one drive with two operating systems, its duel boot?,, or if you run two hdd's, one operating system each, its also duel boot?? i should think, with lubuntu only on 2nd HDD, lubuntu should support, VM, and i only would have to worry about bio's.. <last word may be spelled wrong..
bump

---

### Post by oldfred on 2019-05-09
Its dual boot whether you use one drive or two.
You are booting two systems separately.
The alternative is VM where both systems are running at same time, but that requires more resources, particularly a newer CPU & more RAM.

---

### Post by oneleded on 2019-05-10
^^^^Thanks for the info... i know XP, is a slug/snail. i still have data i want on it. plus my old scanner works on it, 2002 microtec. lubuntu, gets me along just fine online. except for "page hit ranking", but, thats been a problem, over a decade.. i dont understand the phrase, by 1clue, "that at any time, half the information on your disks is unusable", perhaps, i will understand.. i still think, i can run a lightweight dristo, or so,without too much problem, on 2nd. linux hard drive. as ya say though, this system is getting older, exponentially.

---

### Post by oldfred on 2019-05-11
When you dual boot, you only are running one of two systems. So other system is unusable or half not used. You may be able to mount & use data, though.
With VM you still can use it, but your system, I think is too old to run a VM.

I retired XP back in 2010 or 2011 when I got a SSD. SSD required AHCI and XP did not work with AHCI. I was down to one app in XP and just decided the app in Linux while not quite the same, was good enough.

Have seen posts where users find what others are calling 'old' systems that are a lot newer than yours. Often cheap on ebay, one post was user finding neighbor's throwing out 'old' systems that could be fixed & used.

---

### Post by oneleded on 2019-05-13
yea, one of two systems.  i can mount, and reformat, the other drive. i dont know about using data, as yet. i might just shop around a bit on e bay, see what i can find.
i got a Gigabyte, s-series motherboard, i can stick in another cabinet. its newer than the one in the dell 270 optiplex. its is probably, to old  also.

---

### Post by oldfred on 2019-05-13
Some old Dells used non-standard power connectors. Connecting those to standard board fried them.

---

### Post by oneleded on 2019-05-13
thats the gigabyte motherboard information, that is on the box. i dont know what it all means. i not using the dell, for this. it will be a new system.
 it will be an empty cabinet. except for the 500w power supply. the model# is in 2nd picture. ga-ma69gm-s2h...
its a game motherboard. i dont game. it should still be faster then the pentium 4, i have with dell.

---

### Post by oneleded on 2019-05-31
i want to add a puppy derivative, to sdb5. i'm thinking slacko. slacko could be obsolete. this will be before i try to go to a virtual install. i think i got 22gb on sdb5. that should be plenty, and then some.
opinion's?

---

### Post by oneleded on 2019-06-08
> **oneleded said:**
> i want to add a puppy derivative, to sdb5. i'm thinking slacko. slacko could be obsolete. this will be before i try to go to a virtual install. i think i got 22gb on sdb5. that should be plenty, and then some.  opinion's? 
still thinking. appreciate help given, an then some.
The option to edit. i overlooked it here. some site's dont allow this. Oh Well. i will improve on this on my part.  newer puppy, is 64 bits. when i set up my other PC, it run's 32/64. AMD [still, out of date]. i will have limited time on it also, i think, but worth a try.
i have the concept, of multiple dristo's.,, plus multiple drive's on a Hdd. in my case, sdb, 2nd hard drive. i should mark this as solved. yet i haven't tried it as yet. i need a different dristo, for this 32 bit motherboard. i will look around. warm weather is here, more or less. if i can get out, this is my priority. in the meantime, i will look for, a 32 bit dristo, to put on sdb5, to see if it works. then if it dont, work i will have a question. puppy uses a lot, of ubuntu packages. so i will search in this direction, an look for a disto like that. a hint or two, i wont mind.

---

### Post by oneleded on 2019-06-20
if ya dont mind, could ya help refresh my memory, about "root partitioning manager". i did download some distro's, to add one, on sdb5, an run into this, 
probably again. 
would a picture of sdb drive help? i think it is already here, but will re-post it.

---

### Post by oldfred on 2019-06-20
Not sure what you mean by root partition manager.

You can use gparted to manage partitions, but partitions must be unmounted, so normally run from live installer. Ubuntu includes gparted in live installer, but not by default in install as you cannot use it on current drive (mounted partitions). 
You can also download the very newest gparted ISO as a live bootable system.

---

### Post by oneleded on 2019-06-22
Mr. Fred; i probably said it wrong, as usual. i'm trying to load a distro, not virtual, to sdb5. i have to show some picture's, from disks management, and G-parted. the last picture in post #94,, DSCN0080, is not clear enough to help me, explain. only certain times of the "day", i can get a good shot from the screen, with the digital camera. perhaps i should tun off the overhead florescent light at night. mute point.
i'll be back with better screen shot's, an hopefully better dialog. thanks for your patience.
sdb5 is unmounted

---

### Post by oldfred on 2019-06-22
You have BIOS, so you boot installer & choose Something Else.
Then you choose (change button) the partition you want to install into if it already exists.
That new install's grub will take over booting.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

---

### Post by oneleded on 2019-06-24
i think that is where i am getting hung up. i.e...  devise for boot loader instruction..  im getting traces of previous failed attempts, in lubuntu, on sdb1. i need to copy my bookmarks from firefox, saved passwords, from both, firefox/thunderbird. just in case. thats all the backup i need.
 i'll let ya know bout sda drive later.
i might have to disconnect sda drive next time, to feel safe. the next time.
MATE has me install as a superuser. maybe im doing that anyway.
{on the side} MATE has most of the buttons at the top of the page, it causes me to straighten my back. ''for us old one's''

---

### Post by oldfred on 2019-06-24
Becuase you you MBR, you have a four primary partition limit.
But you can make one of the primary partitions an extended partition and then have an unlimited number of logical partitions inside the extended partition. 
You have sdb2 as an extended partition, but sdb5 using all the space inside the extended.
You should first expand the sdb2 partition to take up all the unallocated space as you only have one primary partition left. Normally swap is already inside the extended but does not have to be.

I might first move swap to right end of drive, so that unallocated space after swap  will be in front of swap & then can then also be inside the extended partition. 
Then you should have about 170GB of unallocated space inside the extended and can allocate as many logical partitions as you like.

I backup my Firefox & Thunderbird profiles. The entire xxxxxx.default folder. 
I used to put those folders in a shared NTFS data partition back in 2006 when dual booting with XP. Also copied profiles to XP laptop when traveling & back to desktop when returning. Now have profiles in a shared ext4 data partition, so every install can use same email & bookmarks.

       thunderbird:
[https://support.mozilla.org/en-US/products/thunderbird](https://support.mozilla.org/en-US/products/thunderbird)
[https://support.mozilla.org/en-US/kb/moving-thunderbird-data-to-a-new-computer](https://support.mozilla.org/en-US/kb/moving-thunderbird-data-to-a-new-computer)
[https://support.mozilla.org/en-US/kb/profiles-where-thunderbird-stores-user-data](https://support.mozilla.org/en-US/kb/profiles-where-thunderbird-stores-user-data)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)
[http://www.mozilla.org/support/thunderbird/profile#locate](http://www.mozilla.org/support/thunderbird/profile#locate) 
   Firefox
[https://support.mozilla.org/en-US/products/firefox](https://support.mozilla.org/en-US/products/firefox)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles](https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles)
Firefox files:
[https://support.mozilla.org/en-US/kb/recovering-important-data-from-an-old-profile](https://support.mozilla.org/en-US/kb/recovering-important-data-from-an-old-profile)
[https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data?redirectlocale=en-US&redirectslug=Profiles](https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data?redirectlocale=en-US&redirectslug=Profiles)

---

### Post by oneleded on 2019-06-24
i see how i made my mistake. i'll try to redo this, then report back. thank's
this is how i meant to do this, till i scrambled things.  now i need logical partitions in sdb3, one for data, one for the distro, and where to put the boot loader.
sdb2 is for later on. i think i just want to work within sdb3 for now..

---

### Post by oldfred on 2019-06-24
Grub boot loader goes into MBR, you always specify a drive like sda, never a partition. Last install then takes over booting, although then you can boot into any install & install its grub into MBR, so it is then default boot.
The exception to the rule of never installing to a partition may apply in your case. When grub is installed to a partition it cannot be used to directly boot, only another copy of grub or other boot loader must be used. But you can use your current install to boot a new install by updating its grub menu to add the new install with sudo update-grub.

18.04 or later now use swap file, swap partition not required. But since you have swap partition it will use it, unless you specifically tell it during install not to use it.

---

### Post by oneleded on 2019-06-25
i was on sdb1, when i resized partitions. i think i should have used an outside source. today i got grub issues. since i've already covered that in this thread, it should not be a problem...
when i boot up the PC.. sdb is the lead drive, followed by sda.. so, if i use sdb as boot loader, then update grub, i should be ok?
where can i find the boot repair disk download?

---

### Post by oneleded on 2019-06-26
tonight/this morning, i unplugged sda.. ran Grub 2 with sdb only, plugged in,,,, i dont have any ideal how Grub 2 works. this time i picked the right selection. sdb1 is working. later on maybe not?,,  for now i will leave sda unplugged. i think i need to update grub, then go from there. 
hope this still works, the next time i try it... i gotta eat last night's supper, then snooze. ^^^ i didn't see my previous thread, till i responded, just now. dont know why it took so long to get here. lost in the ether's, i guess..  5:43am  update.. ..
 it takes forever an a day,, at least 4 minutes or so it feels,,,  but, when i start PC, only sdb drive is still there,,  yet,i am here. 1st dry run.

---

### Post by oldfred on 2019-06-26
Grub defaults its install of boot loader to MBR of sda, unless you use Something Else and specify sdb.
So if you only have sdb plugged in, the default to sda will work as only drive it will be seen as sda. But if you plug in another drive and it becomes sda, then you have to specify which drive.

Also if plugging in drives order is usually defined by BIOS and the SATA port order seen by BIOS.
Or lowest port is sda, etc. But XP probably must be sda to work.

---

### Post by oneleded on 2019-06-28
Hey mr. Fred; i am getting the hang of this, more or less. i installed puppy32, PEA, i686 to sdb2. it has grub 4. it is working. i had to reboot so i could, get to sdb1, an update grub. what happens, later in the day i cant say.
 i know i have to get back in bios now, to disable fast boot. i did it before to correct problems, then enabled it again, because it was slow, with fast boot working. Puppy is a different matter..
i am having a problem, figuring out how to make logical partitions, in sdb3. this i suppose, is a different matter..
guess who didnt back up anything again. i could give you a hint..
ed

---

### Post by oneleded on 2019-06-28
i did mess up again, what else in new, so, i will try again...my fist step is to delete sdb2, with puppy, sdb2, then i will continue

---

### Post by oneleded on 2019-06-29
puppy is not on sdb2 anymore, but the  puppy grub4  is still there. so, one drive at a time, i will fix grub,. i figured out how to do logical partitions, on sdb3. i was over-thinking it the 1st time.. puppy has grub 4. im using grub 2, on hdd sda, and hdd sdb. i dont think it will matter.
on my next attempt, i will try to install Puppy, to sdb5, logical partition, from sdb3.. if this is successful, i might think about using VM..
and with luck, i can call this thread solved..
hindsight says if i can do this, the thread is solved, whether i use VM or not..

---

### Post by oneleded on 2019-06-30
OK,, i did make a major mistake. when i installed puppy with grub4, on sdb2, grub4 took over the boot. i uninstalled puppy on sdb2, because i wanted to put it on sdb5. 
grub 4 is still there, on sda, an i cant seen to eradicate it. cd's like grub2 or boot repair dont work. i still can boot, using E12, for lubuntu, or to XP 1st HD, using puppys grub4. it is still there, though that operating system is not. it's not that i mind so much that grub 4 is there. i dont like the ideal, that i cant boot from a cd. i still want to put puppy on sdb5, but if i do that, will i have 2 instances of grub4, i cant get rid of? i can still start the system, PC, with a thumb drive.. maybe that's the way i need to go.
grub4 will let me boot into sda 1st HD with windows, just doesnt see sdb, 2nd HD, with linux. if this sounds confusing to ya'all, even more so to me.

---

### Post by oldfred on 2019-06-30
Is that grub4dos which is based on the old grub legacy, not newer grub2?

Puppy is not a standard install but has some unique requirements, not as easy to dual boot.

---

### Post by oneleded on 2019-07-01
grub4dos is installed on sda. it seems to be blocking my ability to boot from a cd. bios is configure right. at the moment, i dont have a spare usb drive. i tried using F12, to boot to cd also, to no avail.. i think i can still boot with usb, lubuntu 18-4 installed.

---

### Post by oldfred on 2019-07-01
Really should have several USB flash drives.

I ended up with lots as I converted from DVD, and many bad burns. And Microcenter is nearby. Every time I went into store, flash was lower in cost, or larger size for same price or newer USB3 for USB2 prices. So after every trip to Microcenter I have ended up with larger & faster flash drives. Use several for backups, but have Ubuntu installed on several also as emergency boot.

---

### Post by oneleded on 2019-07-02
ya make a good point, and then some, usb wise. or should i say, wiser than me..  (with grub4dos on sda drive, how to i get rid of it), on the side?,, 
i should be able to get, plenty of usb2, drive's, they are near, if not obsolete, yet the public, dont know that, nor care. doubt many know what usb3 is, should ya ask. were i to ask, if ya got a USB drive, round here, no one would know what i was talkin, about, least i explained it. even then, more so ????  oh well, so it goes.
thank you old wise one.  old ed

---

### Post by oldfred on 2019-07-02
Do not buy USB2 anymore.
I found with my old BIOS system a USB3 flash drive in a USB2  was still about 10% faster. And when Microcenter first offered USB3 several years ago, it was a $1 more and worth it. Not sure if any really market USB2 anymore. Some now are the newest USB-C, but you need USB-C ports to fully use those.

[https://www.microcenter.com/search/search_results.aspx?Ntt=USB+Flash+Memory](https://www.microcenter.com/search/search_results.aspx?Ntt=USB+Flash+Memory)
I see they have 16GB USB3 for 2.99 and USB2 for 2.79. And then the USB2 is a rip.

---

### Post by oneleded on 2019-07-03
that is a good deal for me, even is i got to ship. closest to me in in OHIO.
might as well do an online search as well.

---

### Post by oneleded on 2019-07-06
i waited to long to cash in on the sale.. usb3  ya snooze, ya lose.. i still want to get rid of grub4dos. is it true, that if ya run FIXBOOT, on windowsXP, that gets rid of it, sda.. course it already has/had grub2 there. another approach was to use system restore, and i left out, add or remove programs. while it might work, it is newer installations of windows, i dont think it would in XP.
 XP, on sda, is a reserve drive, that i have not, backed up, despite the recommendations. i dont have the proper medium as yet. i got well over 200 bookmarks, on XP. i went through it tonight, deleted near 30, it didnt phase the bookmark list. that was the main bookmark page. 
hope you an everybody has a happy 4th weekend, no mater where ya are. fireworks an beer.. ya can still have fireworks, an beer., or some facsimile thereof..

---

### Post by oldfred on 2019-07-06
I believe it is fixBOOT on Windows, even the new UEFI versions but those re-install UEFI.

With BIOS boot you can install a generic Windows type boot loader syslinux or lilo either directly from Ubuntu or using Boot-Repair and its advanced mode. Choose operating system & drive in advanced mode. Boot-Repair installs syslinux which also is the BIOS boot loader used by the Ubuntu installer. 
Windows BIOS boot loaders only look for partition with boot flag and jump to PBR - partition boot sector for more boot code. Windows has more boot code there, so you only want the MBR part of syslinux if manually installing yourself, otherwise it will also overwrite the PBR of the Windows NTFS partition. Boot-Repair only installs the MBR part if Windows selected.

---

### Post by oneleded on 2019-07-07
thanks. not just for the instruction, but the definition of, "PBR" . i wasnt sure want that meant. only thing i could think of was Pabst Blue Ribbon.. is there a guide, that tells newbee's, what the initials  mean? linux is a new language. most sites dont leave any explanation

---

### Post by oldfred on 2019-07-07
I have some Acronyms defined at the very bottom of the link in my signature.

Old BIOS/MBR boot process.
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by oneleded on 2019-07-08
i flunked english, from the 8th grade on. however, literature, was added to english credit's, when i went to High School 8-12... a dyslexia thingy.. 1-8, common core, they dont care if ya learn or not.. long as when it adds up with everything else, ya pass. nuff of that..
i did write this down,, both drive's were plugged in.. sba-window's, and sdb-lubuntu..  i tried to run boot repair, with both drive's in, just to see what would happen. i got Boot repair 17.04, [i think i found 18.04,, dont have the usb, yet], on dvd+r..  the message, what i managed to copy said;
Disk error 01, AX = 4200, drive 00..  drive 00 is windows 1st HD, i think, 01, should refer to 2nd HD linux..
i have to boot from a thumb drive, with only 1st HD, plugged in, and boot repair on  thumb drive, i think..
still have not got my thumb drives ,as yet..
i am placing an order for usb2 drives, at the price mentioned. it suits my purpose, at the moment...

---

### Post by oneleded on 2019-07-10
so far, this is where i stand;; hope i can explain it well..
when i turn PC on, it boots to windows XP, sda.. that drive has grub2 legacy..and i can chose XP, or grub...
when i use F-12, i can pick sda or sdb.   when i pick sdb, linux, it gives me the choice of booting to sdb-lubuntu, or sda-XP.
i used boot repair, with sdb linux unplugged, and did get rid of grub4..
before i ever got into this last mess.. when i turned on PC, the grub menu was, sdb linux, or scroll down to sda XP.  
the easy fix is to just reverse the order of the hard drives, not through the bios, but the way they plug into the motherboard. or so i think.
but i did have grub, starting with sdb, 2nd hdd.
i will study grub instruction more, maybe it will sink in..

---

### Post by oldfred on 2019-07-10
Not sure if Windows would like your switch of drives. Have not used XP for almost 10 years, but its boot.ini has reference to drive and Windows always assumes it is first (and only) drive.

I would just set sdb Linux as first in boot order in BIOS.

---

### Post by oneleded on 2019-07-12
funny;; 
windows dont like much of anything.. i had grub before, with XP drive, just cant remember how i was instructed to do it.,, it would start with sdb, and the choice to boot to sad,xp,, i mean sda xp..
i had installed, puppy on sdb2, i know.,  an had not used, virtual box as yet. so that is a start. am i at a point where i can mark this as solved, i think the rest is easy, once i get it to boot, the way it was, and control grub better..
i cant set the linux drive as 1st in bios, but i can on the motherboard.. that should prove interesting.. the optiplex 270, does not allow for this.. or, i changed settings, where it doesnt work anymore..
an old machine, and an old explorer, to break it, and see if you can fix it. or, go from norfolk, virginia, without a map to louisville, ky., and see if on the return trip, you can cut your hours down.
linux is way more interesting.,, and ya dont have to worry about falling asleep.

---

### Post by oneleded on 2019-07-14
just a thought;; i only want 1 hdd running at a time.. sda when in a emergency, but mostly sdb. i havent had both drives running at the same time, nor want to.. for me, it would be like trying to ride 2 horses, in the same race... .. i will reread through this again, this week. a lot of nitrogen storm's are supposed to run through this region. [lighting].. i may be trapped inside the house for a few days. 
when sdb runs, i hope to have at least 2 systems, os, on that Hdd.. sdb..

---

### Post by oneleded on 2019-07-17
i have to store this for a moment.. do not reply yet.. i havent figured out how to store it on lubuntu as yet.. questions may follow..ed@ed-OptiPlex-GX270:~$ sudo grub-pc/install_devices
perhaps, i should explain myself.. sda xp is still 1st hard drive,... sdb lubuntu is still 2nd hard drive.. i am working on boot loader instruction, that got messed up, when i installed puppy on sdb2.
puppy installed grub 4.. i did removed puppy, on sdb2, but it left behind grub4. i got rid of grub 4, but messed my boot loaded instruction.. i did have it to where i booted with sdb first.
i have to do this. later i can do this the easy way, and switch the order, by the motherboard. thanks..ed ps.. if i could do it i bios, i would, but my bios wont let me..
April 8 2019, commands taken from post #52

[sudo] password for ed: 
sudo: grub-pc/install_devices: command not found
ed@ed-OptiPlex-GX270:~$ sudo -grub-pc/install_devices
sudo: unknown group: rub-pc/install_devices
sudo: unable to initialize policy plugin
ed@ed-OptiPlex-GX270:~$ -grub-pc/install_devices
bash: -grub-pc/install_devices: No such file or directory
ed@ed-OptiPlex-GX270:~$ sudo debconf-show grub-pc # for BIOS with grub-pc
  grub-pc/postrm_purge_boot_grub: false
  grub2/no_efi_extra_removable: false
  grub2/unsigned_kernels_title:
  grub-pc/timeout: 10
  grub-pc/install_devices_empty: false
  grub2/unsigned_kernels:
  grub2/device_map_regenerated:
  grub2/linux_cmdline_default: quiet splash
  grub2/linux_cmdline:
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/install_devices_disks_changed:
  grub-pc/partition_description:
  grub-pc/install_devices_failed_upgrade: true
* grub-pc/install_devices: /dev/disk/by-id/ata-ST3250310AS_6RY2VVZ4
  grub2/kfreebsd_cmdline_default: quiet splash
  grub2/update_nvram: true
  grub-pc/disk_description:
  grub-pc/kopt_extracted: false
  grub-pc/install_devices_failed: false
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: true
  grub2/kfreebsd_cmdline:
ed@ed-OptiPlex-GX270:~$ sudo lshw -C Disk -short
H/W path         Device      Class          Description
=======================================================
/0/1/0.0.0       /dev/cdrom  disk           DVD-ROM GDR8162B
/0/1/0.1.0       /dev/cdrw   disk           DRW-24B3ST   i
/0/2/0.0.0       /dev/sda    disk           120GB ST3120026AS
/0/3/0.0.0       /dev/sdb    disk           249GB ST3250310AS
ed@ed-OptiPlex-GX270:~$ sudo grub-probe -t device /boot/grub
/dev/sdb1

taken from post #52

ed@ed-OptiPlex-GX270:~$ sudo grub-install --recheck /dev/sdb
Installing for i386-pc platform.
Installation finished. No error reported.
ed@ed-OptiPlex-GX270:~$ sudo update-grub
Sourcing file `/etc/default/grub'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.18.0-25-generic
Found initrd image: /boot/initrd.img-4.18.0-25-generic
Found linux image: /boot/vmlinuz-4.18.0-24-generic
Found initrd image: /boot/initrd.img-4.18.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done

---

### Post by oldfred on 2019-07-17
From your list above this is the drive that grub will reinstall into on major updates.

grub-pc/install_devices: /dev/disk/by-id/ata-ST3250310AS_6RY2VVZ4

If not sure which drive is which:
       to see similar drive info
sudo lshw -C Disk -short

---

### Post by oneleded on 2019-07-17
sdb lubuntu drive..  i think my problem is with the mbr, on sda. i had that trouble with grub4, and i dont believe i corrected it the proper way.

---

### Post by oneleded on 2019-07-25
i reversed the plug ends on the drive, since i couldnt do it in bios. now the 2nd drive, is 1st, and the 1st drive is 2nd, when it boots. so the grub on the lubuntu drive is the first thing i see, on it gives me the option, to boot to the windows drive, if i want. you all told me enough on multiple distro, plus a lot on grub, not to mention other things. its been very informative, an most appreciated. @oldfred, you even put a lot of extra miles on this. im fairly confident i can do this..
plus i know my weak spots. thanks a bunch.. ed
grub has to be updated. first major challenge .. hadnt though of that. posted at 01:22
the names have changed, but the song remains the same. lubuntu is sda now, an XP is sdb.. posted at 02:21
grub is not affected.. so for my next trick, install to /dev/sda5 extended ,, i think i got that right.. posted at 21:41

---

### Post by oneleded on 2019-08-26
the local Radio Shack had a sale, 75% off.  i got there late, but still managed to get $200. or more of stuff. sister bought some stuff, and i paid for it. i spent 300. i got some usb 2 drives, and when i save a copy of this version of lubuntu,[back-up], now on sda 1, i will put what i learned to the test. thanks again for the patience to stick with me..

---

### Post by oneleded on 2019-09-07
i do consider multiple distros solved to my satisfaction.. but in this thread, was the need to back up.. while i am finding plenty of utility's to back up to a flash drive, i would like more instruction..
i dont think i should pursue this on this thread, and, i am sure the info is already here on this forum. i am not able to put in the correct search terms. just a thing i got.. anybody got any pointers?
the need to back up is underrated.. i think most, like me, just dont have the basic skills, to do this. i understand the need too, but not the how too.. i just got to back up lubuntu, which is small, and a thumb drive will work. others may want to back up a whole drive. just saying, on my part. even if i got the backup software, i want to make sure, i know how to use it.

---

### Post by oldfred on 2019-09-07
I do not believe in backing up system. As I will just reinstall.
But I do backup my data & copy my data (which is not really a backup).

I use rsync to copy to different flash drives.
TheFu uses rsync for only those things that rarely change like his media files but uses rdiff for his backups.

Change date to last year to limit search even more
[https://www.google.com/search?client=ubuntu&channel=fs&q=site+ubuntuforums.org+backup&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=site+ubuntuforums.org+backup&ie=utf-8&oe=utf-8)

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[URL="http://ubuntuforums.org/showthread.php?t=1883834"]http://ubuntuforums.org/showthread.php?t=1883834

      [/URL]
 discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
Gui tool:
[http://www.teejeetech.in/p/aptik.html](http://www.teejeetech.in/p/aptik.html)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
More backup info from 1clue
[https://ubuntuforums.org/showthread.php?t=2377810](https://ubuntuforums.org/showthread.php?t=2377810)
[https://askubuntu.com/questions/569679/whats-a-good-back-up-strategy-for-1-desktop-pc](https://askubuntu.com/questions/569679/whats-a-good-back-up-strategy-for-1-desktop-pc) 
     [URL="http://ubuntuforums.org/showthread.php?t=1883834"]
[/URL]

---

### Post by oneleded on 2019-09-08
thanks again, oldfred, looks like i got some reading to do. i can always reinstall lubuntu. so, i just need to back up and copy my data. why didnt i think of that? :-)

---

### Post by oneleded on 2019-10-15
family things going on, so i been slacking off here. mom was 82..
about the only thing i want to save is my book marks, maybe some pictures, and i know how to do that.. now for the interesting question... its a whopper..
i may have to rephrase it a few times.
 
theoretically speaking.
 i got lubuntu 18.04LTS.. i want to do a fresh install, with the bookmarks i saved..
 i also want to install slacko.  
so i reinstall lubuntu 18.04LTS. it has grub 2. 
then i install slacko. it has grub 4. {i havent had the time to figure out how to install slacko, with grub 2..
now i will have grub 4 running the show..
so, when i add another distro, say linux mint, it has grub 2.
will the 3rd distro, take me back to grub 2?? i know the pecking order is changed. mint, slacko, lubuntu..  but.. i want to have grub 2, i believe, running the show..
i think i like grub 2 better..
hope this makes some sense..

---

### Post by oldfred on 2019-10-15
Do not know slacko, but thought slackware used syslinux or similar.
There is no grub4, just original grub whichis now grub legacy and grub2, both commonly called grub. Grub2 has been standard since about 2009.
Actual grub2 versions now are grub-pc for BIOS and grub-efi-amd64 for 64 bit UEFI systems.

Edit- your mention of grub4 must really be grub4dos which is really an old  version of original grub, grub legacy for booting from NTFS partitions or DOS partition. Not sure how other systems may use it.

If MBR, you only have one place for boot loader. So each install will overwrite the MBR with its version of grub. So last install is in control and usually find other installs. Not sure with slackware or other similar systems that use a different boot loader. They may not auto find other installs.

If you want to save bootmarks you need to backup Firefox. Better to backup entire firefox profile or all of /home.

Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) & 
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

Firefox
[https://support.mozilla.org/en-US/products/firefox](https://support.mozilla.org/en-US/products/firefox)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles](https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles)
Firefox files:
[https://support.mozilla.org/en-US/kb/recovering-important-data-from-an-old-profile](https://support.mozilla.org/en-US/kb/recovering-important-data-from-an-old-profile)
[https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data?redirectlocale=en-US&redirectslug=Profiles](https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data?redirectlocale=en-US&redirectslug=Profiles)

---

### Post by oneleded on 2019-10-17
thanks again. slacko is a puppy derivative. Barry someone, i have to look up his last name. linux puppy distro. i may be looking for something that cannot be done.  Puppy linux is old. i like it though.. no accounting for taste is there. :-)
4 weeks Later;;
 Barry Kauler, is the Puppy guru.., that came up with Puppy Linux..
i aint been here in a while, personal problems, but i am back.. 
i backed up firefox bookmarks, but dont remember if i backed up the profile. i'll check that out.  i also copied the desktop, only cause i got some pictures there. i just need to make a copy of my passwords. it doesnt matter that i wrote them down, it is where did i write them down??..
no one uses my PC, because Linux is scary. Boo Hoo. i like it like that...
So,,,
if i install slacko, 1st partition,with grub4dos, the oldest grub, then re-install lubuntu, on 2nd partition, the grub 2 will overwrite, old grub4??
grub 4 did work, with lubuntu.. the last time i tried to install slacko..
as far as Synaptic Package Manager, and doing it over, every time i do, i learn just a bit more.. i may not have to much brains on top, but with repetition, i can fake it.. :-)

---

### Post by oneleded on 2019-12-01
i deleted sda1 lubuntu. i didnt take into account grub. i get; 
no root system is defined
correct from the partitioning table. i tried, but cant do it.
i am stuck for the moment.. it happened before. i dont have any memory of how i got it going the last time.. old and brain dried.. 
at the moment i am running, on the set up disk. i just cant set it up, nor get to sdb windows drive.

---

### Post by oldfred on 2019-12-01
Most of grub is in partition, that you deleted.
Only MBR has the start of boot with grub.
You need to restore boot loader of whatever system you have left or reinstall grub. Boot-Repair is often the easiest way. Otherwise you have to chroot from the live installer.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by oneleded on 2019-12-03
@oldfred: "Most of grub is in partition, that you deleted".

i knew i messed up, soon, after i did it, linux wise.
 i used to do it to windows.. who needs a blue sky, when you can look at the blue screen..,
 i will get windows drive going 1st., so i can talk, then repair/set up linux drive.  thanks, for hanging in there with me, and the rest of you, that put up with me...

---

### Post by oneleded on 2019-12-08
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

lubuntu@lubuntu:~$ sudo grub-install /dva/sda
Installing for i386-pc platform.
grub-install: error: failed to get canonical path of `/cow'.
lubuntu@lubuntu:~$ # grub-install /devhd0    <<<[i made a mistake on this line, i think i need to delete it}
lubuntu@lubuntu:~$ #  grub-install /dev/hd0
lubuntu@lubuntu:~$ 
________________________________________________________________________--

i havent tried as yet to see if this will work. however,
http://
paste.ubuntu.com/p/
myqHHy8TJg

that is what i got when i ran boot repair, ppa. version..
now i cant boot, from the dvd/rom drive.. only usb..  i can still get to windows on sdb/hd1 drive. using F12 option.
i thought about just deleting the sda/hd0 drive and starting from scratch.
i thought this thread was solved, till i messed up, and will mark unsolved for a while. least i get two distros running on my linux drive, maybe three.
so close, yet so far away..  ed

20 minutes later. 
a thought just occurred to me. the dvd/rom drive is older than my computer. maybe it just conked out..

^^^^ the last statement, "20 minutes later", is not correct.. i did something else. i dont know if it was in bios, or somewhere else. where ever it was, i did a good job of it.. i will get here, nothing wrong with the dvd/rom, it will play in windows, just not from a live disk.

---

### Post by oldfred on 2019-12-08
From the live installer you cannot run install grub. That attempts to install grub to live installer, not your install. Many new users find Boot-Repair easier.  That command does work if you are in your install and want to update grub.

You have to mount you system partition which has /boot in it. Or both /boot partition & / if separate partitions. For BIOS type installs. Change example with sda6 to your / partition sda1, sdb1, etc which every it is.
       sudo mount /dev/sda6 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
Please note that the --boot-directory switch is new in Natty and is to be preferred, in case someone tries to tell you that should be --root-directory.

---

### Post by oneleded on 2019-12-10
> **oldfred said:**
> From the live installer you cannot run install grub. That attempts to install grub to live installer, not your install. Many new users find Boot-Repair easier.  That command does work if you are in your install and want to update grub.

You have to mount you system partition which has /boot in it. Or both /boot partition & / if separate partitions. For BIOS type installs. Change example with sda6 to your / partition sda1, sdb1, etc which every it is.
       sudo mount /dev/sda6 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda
Please note that the --boot-directory switch is new in Natty and is to be preferred, in case someone tries to tell you that should be --root-directory.

i like what you are saying. it still got to think a bit, like an ent, in the Tolken books..
"sudo mount /dev/sda6 /mnt" ,gives much room for thought
the / is important with mount point.

[dont answer till i finish writing this, i have to send a picture or two] it wont be long
thanks for keeping me in the loop. i know i am a hard study

---

### Post by oneleded on 2019-12-12
this might be worth an answer. since it is going on 2020. should i update, both Boot-Repair, and the Grub2 install cd? it seems so self-evident,, i didnt want to ask it before.,, and i have put off asking the question., plus the update.. ..

---

### Post by oldfred on 2019-12-12
I use latest LTS or currently 18.04LTS as my main working system. 
I do another install or three to either test changes before including in my main working install or to see what has changed in latest version. 

Just installed daily live 20.04 which will be the next LTS version. I will reinstall before making it may working install as the daily live has many, many changes before final release. Or log files & history of updates gets large.

---

### Post by oneleded on 2019-12-15
some things have been acting strangely lately, with the old computer, my computer.. it got where it wasnt detecting things, as a ROM drive, then the thumb drive. perhaps more..
so i looked it up. this time i put in a better search term. as, bio's wont detect device..  i opened up the PC, checked, and changed a few connectors, then took the battery out of the motherboard, resetting the bios. only way i could do it.. least the thumb drive is back at start-up. that is one thing. the only thing i tested as yet. i will be back, regardless, how can i not.. ed

---

### Post by oldfred on 2019-12-15
I have only had one coin battery fail, but have not kept computer for more than 6 or 7 years.
When coin battery failed, the clock reset to default on every new cold boot or full power off.
So if time is off when you shutdown & then boot, check coin battery on motherboard.

---

### Post by oneleded on 2019-12-17
> **oldfred said:**
> I have only had one coin battery fail, but have not kept computer for more than 6 or 7 years.
When coin battery failed, the clock reset to default on every new cold boot or full power off.
So if time is off when you shutdown & then boot, check coin battery on motherboard.

the windows hard drive has not been able to keep time for a couple of months. i pulled the battery out, so as to reset the bios.
i thought the bios might see my ROM drives again.
it could be more than that, the motherboards were known for capacitor problems in old age . i just feel like i am missing something obvious.
{recheck the plugs from the motherboard again, to the ROM drives}.

---

### Post by oldfred on 2019-12-17
I had an old 7600 nVidia card.
One night I heard a pop, was not sure if computer or outside, but computer kept working.
Next morning my wife could not start it.

Replaced power supply, motherboard & GPU card. Found later photos of other 7600 cards with capacitors popped. Mine looked just like those, some top wide open other just a little open. 

If I had shut system down right away, I probably could have saved replacement of motherboard & power supply.

---

### Post by oneleded on 2019-12-17
> **oldfred said:**
> I had an old 7600 nVidia card.
One night I heard a pop, was not sure if computer or outside, but computer kept working.
Next morning my wife could not start it.

Replaced power supply, motherboard & GPU card. Found later photos of other 7600 cards with capacitors popped. Mine looked just like those, some top wide open other just a little open. 

If I had shut system down right away, I probably could have saved replacement of motherboard & power supply.

capacitors are a problem with air condition units. usually you can just look at one an tell if its bad. i did hvac for years, i know the risks of playing with the power on.
i seen my boss sitting on the ground more than once,(that tells ya something about my boss).. he liked to work on live circuits. every time E did it though, he was in a good mode for a week(this says something too)...
220
every time a power supply went out, PC wise, the pink resistor was involved. though, i had one power supply, under most every capacitor on the board, was cold solder joints, plus the pink resistor was bad.

---

### Post by oneleded on 2019-12-19
the new dvd rw i got didn't match the motherboard. cables were different. i had to get an adapter. its possible it went bad, its also possible, something on the motherboard, just zonked out. i want to say IDE, should have took better notes. the dell is an old one. maybe 2002, optiplex 270.  i should have taken advantage of cyber Monday. i'd rather have my own build, for a PC., then what is sold.
if i put boot repair on a thumb drive, or super grub2, [some facsimile, thereof], could i get the linux drive going., with what you said, pg. 17, post#163..?

---

### Post by oldfred on 2019-12-19
If system is otherwise bootable, supergrub should work.

When I built my "new" system in 2006, I used SATA and was going to buy a PATA IDE DVD drive as SATA was new and DVD a lot more expensive. But store was just loading shelves with new SATA DVD that was only $10 more.

I really, really hate the old PATA drives as I always managed to drop little jumpers or not get them correct. At least newer drives had label with jumper settings. Old drives just had instructions which were soon lost.

       with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)

---

### Post by oneleded on 2019-12-20
i had trouble today.. now beside the ROM drives, the sata drives are not seen. it didnt even start with the usb stick. i can still get into bios, it looks normal. and i did get to run the usb stick eventually. so i gotta question or so..
1. could this be the battery on the motherboard?
2. maybe the bios is corrupt ?  i see no way to fix it, if that is the case. i feel like i am beating a dead horse on this one..
3. this has to do with a persistent thumb drive. i formatted a 32GB to ext4.. then i read, the first part of the drive has to be FAT. so, is this true?
i got plenty of hindsight, seems i get it often :-)
PS i hate those tiny jumpers too.. ya cant see one if ya drop it, and i need special tools to put one it..

---

### Post by oldfred on 2019-12-20
Flash drive has to be FAT32 for UEFI boot of the extracted ISO and used grub2 to boot.
The BIOS boot version uses syslinux which is a Windows type boot loader. 

But some tools use dd or dd under the hood whether BIOS or UEFI, to make a hybrid DVD/flash drive. That has no partition table, but is bootable more like a DVD. To reuse flash drive you have to erase the partition table area on drive as most tools see the random data in that area and get confused and will not read flash drive.

Time for a Raspberry Pi? It probably has better performance than an old system.

---

### Post by oneleded on 2019-12-26
i will look up Raspberry Pi.
 i did find out that the thumb drive has to be fat, on the front end, then you can partition a ext4 partition. i forget who wrote this. i keep running into your name on some linux sites. thanks again.. 
a friend on another site suggested the battery on the motherboard, might be going bad. sure enough, when i checked for errors, that error was there. i dont remember seeing that before. probably didnt look, while in bios, this time i looked. he told me near a week ago.. i shoulda wrote down the part number, when i tried to reset the bios. i had the battery out,
maybe old school reset.. tis an old PC.. i aint no spring chicken neither.. Have a good one.

Day or so later. i put a used, 3022, battery on the motherboard. i keep getting an error code, when i typed raspberry pi. i thought maybe ya got dyslexia, and spelled it wrong. i tried rasberry ph. it didnt work neither.,, then i figured out;
when a new battery is put on the mother board, with windows, operating system, you have to make sure the clock date and year are set, or ya cant search online.. granted its XP, legacy...
anyway, i found it, i got a big grin, when i read about it. Thanks.
days or more later;;
the battery was a 2032, another zig-zag moment. the battery pack in Kroger [grocery chain], was bout $10.oo, 4 Duracell, made in china. the brand new battery, stopped the problem of booting, and having to use the F1/F2, option, every time i booted.. i spent a lot of time looking that up, before i realized, the replacement battery i used, sat to long, though not used, it didnt have enough power.
i just hope i have the proper battery for the Dell motherboard. it is 3V, an the research i did says this is right. it doesnt mean what i read is right. some of those coin batteries can be 7V on motherboards. i learned that also.

---

### Post by oneleded on 2019-12-30
Well;; the coin battery did go bad. i should get a couple of new ones tomorrow. i stole one off another motherboard. my DVD writer-sata, i took it out and put an older writer in. i got my DVD drives back.  the adapter was/had to be bad. i hoped it was something simple i was overlooking. now to get back to business, my linux drive. ;~} vvv

this is 2 days later;
i deleted the linux drive. when the lubuntu installation disk stopped midway through the installation, i had to turn off the computer. that caused a few problems. i finally got the F12 button to work, the USB drive worked. i deleted the linux drive, and installed lubuntu. i ran into a formatting problem, as the drive had the star on it, and it wouldnt allow me to partition it. so
i finally remembered to use the USB drive. when i resized it, sda1 didnt work. i was warned...  that dont stop me though. so when i go to reinstall lubuntu,, i get the same old problem;;
no root file system is defined
device for boot loader instruction....... this is where it gets interesting. ..
i fixed it. i dont know quite how. it is simple.. only if i could remember how i did it. sda1;
 i marked it as ext4, maybe more,, i reformatted it ext4, the most important thing is,, this time,,, " journaling file system ext 4", and the ability to put, /, in the mount point option.
i have seen this come up before, just dont know how i got there the last time, dont know how i got there this time..
it is the answer to, "no root file system is defined"..
since i only came across this 2 or 3 times in 4 years, i cant help anyone else out yet. 
Only i had a functioning  memory..
ya cant have everything but, i think i got my linux drive back. let ya know soon.

---

### Post by oneleded on 2020-01-11
It's been a couple, of long days. i have a ghost  in the machine..  sda3, and sda4. i cant get them to show up at the moment. i should have maybe overwritten the sda drive with  got some pictures, be a few minutes.[ATTACH=CONFIG]284784[/ATTACH], [ATTACH=CONFIG]284785[/ATTACH]  
 the previous configuration of the linux drive sometimes show up..  see;; june 24, 1919.. #123 post.. ever so often i get this, instead of the new linux partition set up.

i think i understand,,  sda3 is a combination of, sda5,sda6, what i have now. 
though this is confusing, i have changed the order, of the sata drives, more than once, do to circumstance. the linux sata drive is dedicated to linux, and the windows sata drive, is dedicated to windows.
sda4 seems to be missing, and it may be of no matter. that is on the linux drive.
now to restore my Firefox book marks.
that may be a new page for installations and up grades. i couldnt have got this far without your help,  oldfred.. thanks again..

---

### Post by oldfred on 2020-01-11
Your sda3 is your extended partition, so you cannot mount or really use it. It is just a container for sda5 and sda6.

If again getting corruption so you cannot mount sda5 or sda5 check in Disks and icon in upper right corner. There is Smart Status which will tell if drive is good or bad. It can run tests, but all I really know is good/bad.

---

### Post by oneleded on 2020-01-14
i understand.. 
sda4 is missing. i think i deleted it, and is really of no consequence, in the long run.. Smart Status showed no problems.. i'm ready too get on with it, and put a solved at the bottom of the page.
the bad CMOS battery sure threw me for a loop.  its been an interesting ride. i believe i'll cross the finish line soon. the odds are getting close to even.. ;~}

---

### Post by oneleded on 2020-01-20
i installed Bionic Beaver/Puppy on sda5.. i didnt install grub when asked. tonight i just run, "sudo update-grub" in sda1, lubuntu partition. Now when the computer boots, i got three choices:
sda1 lubuntu, sda5 bionic pup, or sdb1 windows. i have to mark this thread solved. i still have to try "virtual box".,,, just not with this thread..

Much Thanks

---

### Post by oneleded on 2020-01-22
just an, add to subject line. i got all my bookmarks back. from saving them from the lubuntu installation i had. before i started this journey i never imagined i could do this, i still got a long way to go, with my skills. i did something, that maybe most dont do, as a beginner. it took me long enough..
if i can do this, anyone can, that tries.. a bit melodramatic, but it is so..
i intend to solve all the threads i have posted, i got maybe two left.
then i can start over :-)
1st Drive is formatted ext3. sda1 is lubuntu. sda2 is bionic pup. the rest of drive is empty so far.
2nd Drive is windows xp.
Grub lets me chose what to boot to.  i got room on sda drive, i haven't tried virtual as yet.

---

