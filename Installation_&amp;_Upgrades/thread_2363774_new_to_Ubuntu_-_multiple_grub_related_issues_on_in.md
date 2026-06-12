---
title: "new to Ubuntu - multiple grub related issues on install [i guess it's complicated]"
date: 2017-06-14
forum: Installation &amp; Upgrades
---

### Post by space.gibbon on 2017-06-14
Hello Ubuntuonians,

So i finally decided to check out Ubuntu, but not 100% committing [yet?] as i'm a gamer as well.

I spent countless hours the last 2 days trying to install and probably don't even remember all of the things i did.

I don't like registering at forums just to ask questions and am kind of a "let me fix it myself" person, but seriously i'm at the end of the do it without asking for help route.
From this point i really hope somebody here can take me to my goal of properly running Ubuntu Studio next to Windows 10.

 Here's what we're working with [a pretty old machine and probably unusual combo]:

- Phenom 2 X4 955 BE, 8GB DDR 3 Ram, HD7870

- 1 x 500GB internal HDD [sda]
   - 2 NTFS partitions --> Win10 & it's stuff

- 1 x 1TB external HDD [sdb ---> 3 partitions in total]
   - 1 NTFS partition BIG
   - 1 swap disk/drive(?) partition 16GB
   - 1 Ubuntu partition 200GB


Current state:

After not being able to install the bootloader no matter how often i tried different locations for install etc, i decided to "continue without a bootloader and install manually"

I thought i actually came pretty far with it, basically looking at that "Configuring grub-pc" screen in the terminal - however there is no device to select to install to.. just an <Ok> symbol which i dont even know how to "click".

And i think here is where the bigger problems begin:

When opening gparted, all the symbols [path, folders, files] related to sdb [my ubuntu install] will disappear from the desktop, gparted will show only sda related partitions.
 
Closing down gparted, all the sdb related stuff re-appears on my desktop!

When selecting "install Ubuntu Studio" from the Live DVD and choosing "something else", i can clearly see that Ubuntu is installed on sdb as per my requirements, back in "try Ubuntu without installing" [because no bootloader for the sdb install], the issues as described above re-occur..



Thank you for reading and possibly giving me an idea on how to proceed.

Also, let me know if you need any more info, i read a lot about fstab being requested etc [mine looks pretty empty]

---

### Post by slickymaster on 2017-06-14
*Thread moved to **Installation & Upgrades**.*

---

### Post by oldfred on 2017-06-14
Have you turned off fast start up? It leaves all NTFS partitions hibernated and then all Linux tools will not work with those partitions. So gparted cannot resize or see it.
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

Is system UEFI or BIOS? Or is Windows installed in UEFI or BIOS boot mode.Newer hardware is all UEFI in last 5 years.

---

### Post by space.gibbon on 2017-06-14
> **oldfred said:**
> Have you turned off fast start up? It leaves all NTFS partitions hibernated and then all Linux tools will not work with those partitions. So gparted cannot resize or see it.
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

Is system UEFI or BIOS? Or is Windows installed in UEFI or BIOS boot mode.Newer hardware is all UEFI in last 5 years.

Thank you for your reply.

Disabled fast start up?
Indeed i did turn off fast start up using a .bat file. I just confirmed it's still disabled via the method described in the first link - looking good [disabled].

BIOS or UEFI?
The complete system runs under the old CMOS/BIOS, no UEFI here [chipset was first released in 2009 or so.]

---

### Post by oldfred on 2017-06-14
With Windows on internal drive you keep the Windows boot loader on the internal drive.
And  you install the grub2 BIOS boot loader to the MBR of the external drive (sdb?).
Then in BIOS set external drive as first in boot order. If external disconnected BIOS will then use internal drive to boot.
Ubuntu default installs, install grub to sda or first drive, typically overwriting your Windows boot loader. 
If you did not use Something Else, which is the only install option that lets you choose where to install boot loader, then you need to restore boot loaders.

If you can boot into Ubuntu on external, install grub to sdb/external drive first. And check that you can boot from it. Then restore Windows boot loader to internal drive with Windows repairs. Best to have Windows repair disk with repair console and Ubuntu live installer always available. Windows on updates likes to turn Fast start up back on.
       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by space.gibbon on 2017-06-14
Thank you again.

The windows bootloader sits on Win C: [sda - mbr, C: is sda1] and works fine, no problems booting directly into Windows.

Boot order in BIOS is set as followed:
1. SATA 3 ATAPI DVD ROM drive [set for booting via Live CD]
2. USB external HDD [sdb, on which's mbr i need to have the grub2 installed afaik. sdb5 is swap, sdb 6 is Ubuntu install]
3. SATA 1 internal HDD [sda, which loads perfectly fine after the other options failed as described in this post.

I tried the "boot-repair" tool yesterday, it apparently has no data to work with / can't find stuff to repair because the bootloader installation always failed].

I tried many different ways of installing the bootloader, last procedure was:

"Something else" --> changed bootloader install location to "sdb" mbr.  //// install runs fine until it tries to install the bootloader, at which point it always fails no matter if i set it to be installed to sda or sdb, mbr or any partition, always same error message.

I will try the steps described in link 2, section "via the LveCD terminal" and come back with results [will take a while because i have to leave the house for a few hours before being able to work on this again].
Apparently this will write new grub files directly into the mbr rather than trying to repair something which isn't installed - hope is restored.

Additional info i failed to mention before:
- self-checked the LiveCD, no issues found.
- downloaded the latest stable release 17.04 directly linked the official Ubuntu website. 
- changed gai.conf file so that IPv4 will be preferred over IPv6 because otherwise it wouldn't connect to the server upon "sudo get-apt update"
- SATA 2 is currently disconnected as it's HDD often fails and would probably disturb the install process

---

### Post by ubfan1 on 2017-06-14
Confirm that the partition table used on the external disk is DOS, not GPT.  Or if it is GPT, that you have a small (1-2M) partition flagged grub-bios (no format needed).

---

### Post by space.gibbon on 2017-06-14
> **ubfan1 said:**
> Confirm that the partition table used on the external disk is DOS, not GPT.  Or if it is GPT, that you have a small (1-2M) partition flagged grub-bios (no format needed).


According to Windows [Disk Management --> device properties] the partition style is MBR, not GPT.

This appears strange because a quick research showed that apparently MBR disks can be up to 2TB only, and everything above that would be displayed as unusable, unallocated space within Windows.
However, even after setting up the partitions there's still more than 2.5TB left and usable in Windows [the NTFS part, sdb1 if i recollect correctly - will start Ubuntu live disk shortly and update if the number is different].
Any idea on how that can be?


Also, i am not sure on how to convert to GPT and what "flagging" a partition means, but will do further research on that as well.

Of course i appreciate your assistance here as well.

I will try "Fixing a broken system" now as linked above by oldfred, and as stated earlier, come back with results.

Thank You!

---

### Post by space.gibbon on 2017-06-14
> **space.gibbon said:**
> 

I will try "Fixing a broken system" now as linked above by oldfred, and as stated earlier, come back with results.



Well, here is what i tried:

1. booted up from the LiveCD into the "try now" mode
2. mounted all sdb related partitions, i can clearly see Ubuntu related files on the 200GB sdb6 part
3. again edited gai.conf via terminal to prefer IPv4 connections
4. installed gksudo at some point because i thought i needed it
5. followed steps from: 
    [URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System

[/URL]    Section "Fixing A Broken System - Via the LiveCD terminal"

a) sudo fdisk -l
> 
Disk /dev/loop0: 2.9 GiB, 3081154560 bytes, 6017880 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x4a658b2d

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 511078013 511075966 243.7G  7 HPFS/NTFS/exFAT
/dev/sda2       511078400 511999999    921600   450M 27 Hidden NTFS WinRE
/dev/sda3       512002048 976769023 464766976 221.6G  7 HPFS/NTFS/exFAT


Disk /dev/sdb: 2.7 TiB, 3000558944256 bytes, 732558336 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00028375

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1             256 679343103 679342848   2.5T  7 HPFS/NTFS/exFAT
/dev/sdb2       679343358 732558079  53214722   203G  5 Extended
/dev/sdb5       679343360 683342591   3999232  15.3G 82 Linux swap / Solaris
/dev/sdb6       683342848 732558079  49215232 187.8G 83 Linux

What does "disk /dev/loop0" mean? i Have no such drive installed afaik, just sda and sdb [both listed as well]


b) sudo blkid

> /dev/sda1: LABEL="Win" UUID="0862D2E562D2D692" TYPE="ntfs" PARTUUID="4a658b2d-01"
/dev/sda2: UUID="4688D86788D856D1" TYPE="ntfs" PARTUUID="4a658b2d-02"
/dev/sda3: LABEL="Gamez" UUID="3AB2F050B2F011DD" TYPE="ntfs" PARTUUID="4a658b2d-03"
/dev/sr0: UUID="2017-04-12-04-07-51-00" LABEL="Ubuntu-Studio 17.04 amd64" TYPE="iso9660" PTUUID="1283d997" PTTYPE="dos"
/dev/loop0: TYPE="squashfs"
/dev/sdb1: LABEL="3L3M3NTZ" UUID="54D8D96AD8D94ABE" TYPE="ntfs"
/dev/sdb5: UUID="a62f7609-4327-4b14-bd6d-640e15b001b1" TYPE="swap"
/dev/sdb6: UUID="869c7029-d56b-4a0c-ad89-110e3495f7dd" TYPE="ext4"
/dev/sdb2: PTUUID="4dcb0e9f" PTTYPE="dos"


c) sudo mount /dev/sdb6 /mnt

no output, probably because i mounted it prior in via the desktop environment


d) sudo grub-install --boot-directory=/mnt/boot /dev/sdb

> Installing for i386-pc platform.
grub-install: error: cannot find a GRUB drive for /dev/sdb6.  Check your device.map.


i386-pc platform? i remember my dad having one, but i thought that while my machine is old, it's still a quadcore so i assume this should display something along the line of x64-pc platform?



Anyways, i checked my device map using

> gksudo gedit /boot/grub/device.map 

because i've seen somebody else on another forum apparently had luck with simply adding a missing HDD in there.

However the result i got looked a lot different from what the person posted:
> (gksudo:27384): GConf-CRITICAL **: gconf_value_free: assertion 'value != NULL' failed

the word CRITICAL was also highlighted in bright pink font in addition to allcaps.

From what i can see now checking google results it appears that my root is missing / not installed / corrupted?

Any further advice?

---

### Post by oldfred on 2017-06-14
Loop device is your flash drive. Often an unformatted device and depending on how you created flash drive installer it may look unformatted. The dd or similar copy to flash is a hybrid ISO/flash configuration that is not a standard partitioned drive.

You get various errors using gksudo, best to ignore. Or better use text editor.
sudo nano path/file 

The reference to i386-pc is for Intel/AMD BIOS type system, not specific processor.

Real issue is that you have attempted to use MBR(msdos) partitioning on a drive over 2TB. That converts drive to only 2TB and rest is unusable.
You need to use gpt partitioning.
You may be able to convert, but really better to start over. You need to have full backup of all your data, anyway, as conversion may not always work.
 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html) 

Newer gpt drives use UEFI for booting if you have newer UEFI hardware. It looks like you have a BIOS/MBR install of Windows on sda, so still better to have Ubuntu in BIOS boot for now. But if in future you want UEFI, you need to have an ESP - efi system partition at or near beginning of drive. I partition all new drives even larger 32GB or more flash drives with gpt and include both an ESP and bios_grub as first two partitions.

To boot in BIOS mode from gpt, you will need to have a tiny 1 or 2MB unformatted partition anywhere on drive. Not sure why grub is not installing since drive is 2TB and MBR as standard MBR, but it may also see it should be gpt.

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

---

### Post by space.gibbon on 2017-06-15
Let me recap the steps i have to take in order to be on the safe side [BIOS boot it is]:

1. backup data from 3TB external HDD
2. Convert 3TB external HDD from MBR to GPT following the link provided by you
3. set up new partitions as followed
 - sdb1: 25GB ext4 \\ mount point: / [--> Ubuntu install]
 - sdb2: 2MB no format \\ no mount point / [--> so grub can install properly /// not sure how to do that yet, just leave unallocated space?]
 - sdb3: 2GB ext4 \\ swap   [---> i've seen that recommended size for Swap partitions would be 1.5-2x the size of the RAM, which would add up to 12-16GB [8GB RAM].. i'm still good to go with 2GB? I have no issues allocating much more if it helps]
 - sdb4: 200GB ext 4 \\ mount point: /home [--> extra space for Ubuntu / Linux related files]
 - sdb5: big chunk TB NTFS \\ mount point: /primary [--> for all those files that are on the HDD now, mostly [audio related] media, windows prog files, diverse backups of previous systems, personal files etc etc]

4. install ubuntu, point bootloader install path to sdb directly, not sdb1 or sdb2 etc.

5. be happy that i can finally dual boot and start learning ubuntu

I will receive sufficient storage space to backup my files within the next 1 or 2 days, but the whole process will take a while.

Therefor i will report back here ASAP - whenever i'm done, or -if i'm not done by that time- in 1 week to let you know i'm still on it [as in this thread is still active].

Thank you again for all your help and your patience!

EDIT: i just figured that it's either sdb2 or "unallocated space" for the tiny 2MB part.. i surely need more info on how to do that

---

### Post by oldfred on 2017-06-15
I prefer to partition in advance with gparted.
And if drive will ever be used with a new UEFI system in future best to include the ESP. I normally suggest 400 to 600MB which is still small with 3TB drive. But windows only creates 100MB ESP and that has room for both Windows & Ubuntu.

I would make ESP & bios_grub first two partitions. Those normally would never be used and then would not possibly be in middle of drive and in way of other changes. I then also put swap at very end of drive, so it is out of way also. I often do not fully partition drive but leave some room so I could move or expand or later add other partitions.

With parted you just create a FAT32 partition and right click add boot flag to make it an ESP.
And then create a 1MB unformatted partition and right click, add bios_grub flag. Since unformatted gparted will always show it as an error, but with gpt it has an assigned GUID and gparted should not be showing it as an error.

---

### Post by space.gibbon on 2017-06-17
Hello again oldfred,


Situation changed a lot, i didn't have to get through the hassle of backing up TBs of data, converting the drive etc.

My brother told me that i still had an old 2.5" sata HDD [5.400RPM] laying around at my parents' place, which i totally forgot about [was from my old laptop which died years ago and is scrapped by now].

Eventually i ended up connecting this drive to my mainboard, clicked "-" a cpl of times [to create 1 big bulk of free space], created root, home and swap... and the install + grub went through no problems!

Had to change the CMOS battery because apparently i had Legacy USB mode off and no PS/2 KB laying around, resulting in a "dead" kb prior to OS boot [bios, grub]..

Writing this from of my Ubuntu install [not LiveCD version], super happy i got everything working now.


Once again, thanks you for all your support, even though the solution came somewhat unexpectedly from another side [just take another HDD]..

You are one amazing person, and i surely learned a lot about file systems etc, which might come in handy in the future!

Will change this thread to solved.

---

