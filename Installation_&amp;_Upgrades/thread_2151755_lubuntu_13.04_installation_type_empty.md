---
title: "lubuntu 13.04 installation type empty"
date: 2013-06-05
forum: Installation &amp; Upgrades
---

### Post by gjv777 on 2013-06-05
I tried to install lubuntu 13.04 on a system with a 80 GB HD from both a USB drive using unetbootin as well as a burned cd.
The HD was unformatted at first, pre-formatted on the other tries with a 15 GB ext-4 for lubuntu, 1 GB swap and 65 GB for /home.

Al tries fail at the same point: after selecting the language and the screen for checking wether enough disk space and internet are available,
I am supposed to get to choose what partitioning type I would like to use. This screen does not appear.
Instead the next screen is shown (what otherwise would have been shown if I had chosen "Else" in the partitioning choise screen perhaps?)
showing me the option to change the partitioning. Only thing is, there is nothing to choose from. My disk is not shown, I cannot choose it from a list. Nothing.

I'm pretty sure the disk is fine, as I used it yesterday with Win XP installed. What is going wrong?

Cheers,
GJ

---

### Post by ajgreeny on 2013-06-05
Are you sure the .iso file you used to make the USB or to burn the CD is good?  Have you checked the md5sum against the listed values at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")?

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]gjv777; And another thing ...

Can you boot the install medium up to and run in the "try ubuntu" mode and is the machine fully functional in this "try ubuntu" mode ?
[/COLOR][INDENT][COLOR=#000000]
it is all a learning experience

[/COLOR][/INDENT]

---

### Post by gjv777 on 2013-06-07
Thanks for your responses, i've done some more testing:

* Verified the md5 checksum, no problem here
* Ran Lubuntu in "Try Lubuntu" mode; this is fully functional, i'm even able to enter disk management and make partition changes to my disk!
* Went thru the crash log and found the following link in it: [http://bugs.launchpad.net/bugs/1058415]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1058415") this tells me something about a raid controller detection, which is weird cos i have none present.
* Tried to install using F6 option nodmraid, still the same result

Next step: trying to install full Ubuntu, maybe it's a driver issue cos of the "lightweight" a IDE driver is missing in Lubuntu?

I'll keep you updated on the results

Cheers,
GJ

---

### Post by Bashing-om on 2013-06-07
[COLOR=#000000]gjv777; Hey ;
I just completed a install of lubuntu 13.04 that was a challenge... what I wound up doing, after a failed install attempt, was zeroing out that hard drive (going to extreme in my case), choosing the "nomodeset" option and not accepting to install updates or 3rd party software. Third try for me was the charm; installed without a hitch. [+ google-chrome and my wife is a happy camper !]
edit: Oh! once the installer crashed when I tried to use a capital letter in the "username" !
[/COLOR][INDENT=2][COLOR=#000000]
frustrating to keep trying, lesson: do not give up
 [/COLOR][/INDENT]

---

### Post by gjv777 on 2013-06-08
The full Ubuntu install gave the same result, so it's not a driver issue.
I also tried the nomodeset option, but that didn't help either
Think i'll try a different HD if i can find one, or see if a BIOS update is available

GJ

---

### Post by sudodus on 2013-06-08
Welcome to the Ubuntu Forums :-)

Please tell us about the computer: Brand name (if any), motherboard, CPU, RAM (size), graphics chip/card, wifi chip (if any). It might help us give advice.

***Please do the following and post the output of the specified commands, when you are running live "Try Lubuntu"!*** Put the output between code tags manually or mark the output and use the # icon at the top of this window

[noparse]```
output
```[/noparse]
 
to get output like this
 
```
output
```

1. Mount all partitions that you can mount using the file browser

2. Run these commands (and post the output)

```
 sudo fdisk -lu
```
```
 sudo blkid
```
```
 df
```
```
free
```

I think you might have a problem with too low RAM, but I don't know yet. With more information, I and other people too can suggest what to do.

---

### Post by gjv777 on 2013-06-11
Hi sudodus, before I read your reply i tried something different.
I attached a usb portable drive to my pc and was able to install Lubuntu without any hassle.
I figured that it might work to clone the usb disk to my hd and tried to with clonezilla.
Clonezilla resulted in an error about being unable to write to the hd. 
So I stripped another pc of its hd, replaced my thought-to-be-fine hd and Lubuntu is installing right now!

I'm still curious what's wrong with the first hd, i will try to figure it out since i had been using it with XP running fine.

Thanks for all the help, really appreciate it!


Cheers,
GJ

---

### Post by sudodus on 2013-06-11
If you show us the output of at least 

```
 sudo fdisk -lu
```

but maybe also

```
 sudo parted -l
```

run when the 'maybe bad HDD' is connected, and post the output, we might be able to help you find the error.

---

### Post by Bashing-om on 2013-06-11
[COLOR=#000000]gjv777 -and all;;
Another thought pops to mind... that disk may have embedded "Raid meta" data on it.. would't take much to install ubuntu's raid tools and see if the supposed meta data is removed.
[/COLOR][INDENT=2][COLOR=#000000]
whatcha think ?

[/COLOR][/INDENT]

---

### Post by sudodus on 2013-06-11
Yes, [COLOR=#000000]embedded "Raid meta" data is [/COLOR]a known issue :-)

---

### Post by gjv777 on 2013-06-12
So, here is some additional information:
CPU: AMD Athlon XP 2500+
Memory: 2 GB DDR2
Graphics: Geforce FX 5200
HD: Maxtor 6Y080L0 80GB

The 2 Gigs of ram should eliminate a memory issue i think

And the output of the commands while running in demo mode from a usb drive:

sudo fdisk -lu
```

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ce532


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    34877439    17437696   83  Linux
/dev/sda2        34879486    39069695     2095105    5  Extended
/dev/sda5        34879488    39069695     2095104   82  Linux swap / Solaris


Disk /dev/sdb: 8059 MB, 8059355136 bytes
255 heads, 63 sectors/track, 979 cylinders, total 15740928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x069adf78


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    15740927     7870432+   b  W95 FAT32

```

sudo blkid
```

/dev/loop0: TYPE="squashfs" /dev/sda5: UUID="85dde858-0f10-4c26-8d05-f2ab697d2f66" TYPE="swap" 
/dev/sdb1: LABEL="##GJV_8GB##" UUID="32E6-14EC" TYPE="vfat" 

```

df
```

Filesystem     1K-blocks    Used Available Use% Mounted on
/cow             1032472   45948    986524   5% /
udev             1021344      12   1021332   1% /dev
tmpfs             206496     736    205760   1% /run
/dev/sdb1        7854048 2429364   5424684  31% /cdrom
/dev/loop0        642560  642560         0 100% /rofs
none                   4       0         4   0% /sys/fs/cgroup
tmpfs            1032472     272   1032200   1% /tmp
none                5120       0      5120   0% /run/lock
none             1032472     136   1032336   1% /run/shm
none              102400      16    102384   1% /run/user

```

free
```

             total       used       free     shared    buffers     cached
Mem:       2064944     938012    1126932          0     131828     538904
-/+ buffers/cache:     267280    1797664
Swap:            0          0          0

```

sudo parted -l
```

Model: ATA Maxtor 6Y080L0 (scsi)
Disk /dev/sda: 82.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  17.9GB  17.9GB  primary                   boot
 2      17.9GB  20.0GB  2145MB  extended
 5      17.9GB  20.0GB  2145MB  logical   linux-swap(v1)




Model:  USB Flash Memory (scsi)
Disk /dev/sdb: 8059MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  8059MB  8059MB  primary  fat32        boot

```

I don't know how to test for Raid meta data on the disk.

GJ

---

### Post by sudodus on 2013-06-13
The computer should be able to install and run any Ubuntu flavour without problems according to the specs.

It seems that the file system of the first partition /dev/sda1 is corrupted, because no file system is recognized. The size is 17.9GB and it has a boot flag. And there is a small extended partition, that only contains a swap partition, which looks good.

But the rest of the drive is not allocated.

How does this correspond to you notion of the drive? You wrote that the drive worked with Win XP installed. Did you plan to overwrite it, did you shrink it, or did you overwrite it by mistake?

Before doing anything else, you should consider some rescue operation unless you planned to overwrite it.

I will not be able to help during the next 6-7 hours, so [COLOR=#ff0000]@anyone else: feel free to jump in and help[/COLOR]

---

### Post by gjv777 on 2013-06-20
The disk was cleared on purpose, no worries.
The partitions were created by clonezilla when i tried to clone the usb disk to the hd; it failed after creating the partitions, but before cloning the data.
So some sort of access was allowed to clonezilla.
then i figured that Lubuntu installer would be able to use these partitions, but again no go.
After that i listed the out put of the commands to this thread.

At this moment i am at a point i think it is wise to just admit that this is an ex-disk and discard it in the apropiate bin next to my desk..

---

### Post by Bashing-om on 2013-06-20
[COLOR=#000000]gjv777; Hi again...
Might I suggest before throwing out that disk.

Zero out the disk with the "dd" command -> fresh state, starting all over;
--if dd squawks, need to look at the embedded data on that disk --
With the command line tools, make a new partition table and format the partitions:
[/COLOR][https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
Take a look at the disk in GParted;
install lubuntu onto the preset partitions that you made earlier.[INDENT]
been there done that -> still using that old disk

[/INDENT]

---

