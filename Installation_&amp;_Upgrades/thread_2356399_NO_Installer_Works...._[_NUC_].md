---
title: "NO Installer Works.... [ NUC ]"
date: 2017-03-22
forum: Installation &amp; Upgrades
---

### Post by greengalaxy on 2017-03-22
I recently built a NUC Intel mini PC, partitioned it, and installed 64bit Windows7 no problem. (choosing Legacy mode in BIOS).   I left other partitions for Linux.   I chose the NUC because it is known to be the best hardware to work with Linux.   Many have put Ubuntu on it.   I told everyone at the office that I was going to go Linux.  But weeks later when they ask, I have to tell them that none of the installers would even work :(
Originally, after a lot of research I chose LXDE, because it looks more like Windows, and because it is fast,light, and not bound up with lots of other software (I prefer to choose my own.)  So, Lubuntu.    
But the installer always freezes at same point.   Yes, I ran the option to "Check Disc For Errors".   I also tried multible versions of Lubuntu, most recently the LongTerm release, LTS 16.10. (64bit)   I put them on USBstick using Rufus.  When that failed, I tried another USBstick, using 'LinuxLive USB Creator'.  It failed, so I burned it to DVD.   I always 'verified' the images.   They always boot, but after I get to the screen that says 'Preparing to Install Lubuntu', and asks whether I want to 'download updates +3rd party software for graphics, etc', and I click the 'continue' button, it just freezes.  It doesn't matter whether I chcck the checkboxes for those 'download updates +3rd party', or leave them blank.    It always freezes.   I usually let it 'run' for about half an hour after clicking 'continue', but nothing happens.  
So weeks later, no Lubuntu installer has worked.   I've installed Windows close to 100 times at work over the last decades, and never had an issue.
Is my using the 'legacy BIOS' a problem?  I read that Ubuntu has some bugs/issues with UEFI, and I've already installed Win7 as Legacy.   
Another thing:
The .iso file for 64bit says amd64!!  The main download page says click here for 64bit, but the .iso file name itself says amd64.  Moreover, the OFFICIAL Ubuntu Documentation says there is no 64bit working for intel, only amd. (SEE: [http://cdimage.ubuntu.com/lubuntu/releases/16.10/release/](http://cdimage.ubuntu.com/lubuntu/releases/16.10/release/))   But forum users say the official documentation is incorrect  (even though all versions going back many years remain incorrect in the docs!!) and that it does work.   However, nothing has worked for me.  
So my month long intro to Linux has been nothing but failures.
Any suggestions?
Do any ancient versions of installers work (like Lubuntu 14 LTS or before?   And can they be updated once installed? 
Do other distros have installers that work with intel?   Would Linux Mint work? But they don't use LXDE (:    
Thanks for any help!
—-

---

### Post by QIII on 2017-03-22
Hello!

First, let's not get wrapped around the axle about the name.  AMD was the first to bring a 64 bit instruction set and hardware to the commercial market and the name stuck as a convention.  It will work just fine for Intel processors.

Could you tell us the exact model of your NUC.  Some have worked better than others for Linux users.

---

### Post by greengalaxy on 2017-03-22
Intel NUC NUC5i5RYH, with Intel Core i5 Processor.  (It has 2 drives inside it.   I'd like to install on the main drive, which is SSD.)
            (PS: yeah, I know amd invented 64bit, I was one of the first to get it.  But that was nearly 10 years ago.  It seems that the official Ubuntu release pages, should be corrected and updated, as they still say amd only. )

---

### Post by greengalaxy on 2017-03-22
Note that according to both the Intel NUC sites' documentation, AND all the user comments on the amazon page for this Intel NUC NUC5i5RYH, both Ubuntu and Mint  and Arch Linux, etc all install with it.

---

### Post by QIII on 2017-03-22
"amd only" or "only amd"?  They only give the option for downloading AMD64 because that it what the image is called.  AMD64 is still a widely used convention, although there is also x86-64.  It's a naming convention.  We could call it "Bob" for all it matters.

Anyway, according to [this]("http://www.intel.eu/content/www/eu/en/support/boards-and-kits/intel-nuc-boards/000005628.html"), users have reported that Ubuntu works with that NUC.  How recent the versions used I don't know.

Let's just wait and see if someone stops by with a good answer for you!

Cheers!

---

### Post by Irihapeti on 2017-03-23
Have you tried the Lubuntu alternate installer? That uses a different and more basic graphics driver. It also uses less memory, though that is not likely to be an issue on the NUC.

---

### Post by jeff666 on 2017-03-23
legacy mode is defiantly what you want for beginner, (double check that it is on and also read through your bios menu for clues take the time to research and understand it all). 
Did you say to unmount all devices in use during installation (before partitioning)? if your device has limited enough ram and is unmounted from the usb it won't load enough of the install files and crash. give that a try if lubuntu doesn't have that option during install try using Ubuntu server( you said you like choosing your own software that will give you nearly complete control as well). Hopefully that helps ill check back i might have a few more idea for you.

---

### Post by sudodus on 2017-03-23
I have an Intel NUC 6i3 SYH (slightly different from yours), and it boots very nicely into the current Ubuntu family operating systems, including Lubuntu, both in BIOS mode and UEFI mode.

> They always boot, but after I get to the screen that says 'Preparing to Install Lubuntu', and asks whether I want to 'download updates +3rd party software for graphics, etc', and I click the 'continue' button, it just freezes.

I usually avoid  'download updates +3rd party software for graphics, etc' during the installation. After installing successfully, I update & upgrade when running the installed system. I suggest that you try that method.

-o-

Please post the output of the following command lines. It will help us help you.

```
df -h
sudo lsblk -f
sudo lsblk -m
sudo parted -ls
```

Please put the output of the commands within [noparse]```
tags
```[/noparse] to make it easier to read: Click on the red button **[COLOR="#FF0000"]Go Advanced[/COLOR]**, mark the text and click on the **#** icon above the editing window (or do it manually), like this:

[noparse]```

your output line 1
line 2
line 3
...

```[/noparse]

Notice that you can mark (press the left button while moving the cursor) and paste (press the middle button or wheel to paste) from a terminal window to the editing box of Ubuntu Forums.

---

### Post by greengalaxy on 2017-03-23
thanks for replies!  i'll look into Ubuntu server and the 'alternate Lubuntu' installers .
@sudodus: How can i enter in the command lines if i can't install lubuntu?  Or can I get a terminal window from the installer?? I'll try tomorrow.  

@jeff66: I have 16gb RAM, so this isn't a problem.  (Re: unmount all devices in use during installation:  only the monitor, usb keyboard, mouse, and 2 internal drives were attached.)

---

### Post by sudodus on 2017-03-23
My idea was that it might work better if you *do not* 'download updates +3rd party software for graphics, etc' during the installation.

An alternative is to install from an image of an already installed Ubuntu minimal system, according to the following link. It would make you independent of the regular installer. I have such a system working in my NUC, so it is likely to work in your NUC too.

[help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by jeff666 on 2017-03-23
ill answer your question @sudodus just press ctrl+alt+F2 that will give you a shell. 

Your using a usb stick to install right? The usb is mounted so files on it can be written to ram once the installer loads, during partitioning it will automatically unmount it (so you can actually do the install on the same usb stick you used for the live installer), depending on how your processor, ram, live installer works it may not write all the files it needs to ram because at the time it thinks it won't need them.  During the install it may need them and crash (so my previous post was wrong it might not even matter the size of ram). Give Ubuntu server a go make sure you don't unmount disks in use before partitioner, ill bet you it works. If the partitioner won't allow this You can unmount at the partitioner, when the partitioner is done enter shell and remount it (or also just unplug the usb stick after the partitioner and the plug it back in). I have had the same problem with kali linux because of all the tools kali comes with.

Good luck hope it goes well those NUCs look pretty awesome, Intel graphics, Intel wireless card you should have no problems once this gets installed!

---

### Post by greengalaxy on 2017-03-24
Hi.  The LIVE version of Lubuntu works.    From its treminal I ran the commands and got:

```

lubuntu@lubuntu:~$ 
lubuntu@lubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  9.7M  1.6G   1% /run
/dev/sdc1       1.9G  1.9G   47M  98% /cdrom
/dev/loop0      853M  853M     0 100% /rofs
aufs            7.8G  258M  7.6G   4% /
tmpfs           7.8G   53M  7.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
tmpfs           7.8G  4.0K  7.8G   1% /tmp
tmpfs           1.6G   28K  1.6G   1% /run/user/999
/dev/sdb5        28G  2.4G   26G   9% /media/lubuntu/SHAREDFAT32
/dev/sda6        81G   35G   46G  44% /media/lubuntu/750g-GsDataNEWInternal
/dev/sdb1        25G  7.3M   24G   1% /media/lubuntu/Linux
lubuntu@lubuntu:~$ sudo lsblk -f
NAME   FSTYPE  LABEL             UUID                                 MOUNTPOINT
sdd                                                                   
|-sdd9 ntfs    D15TB-HugeDesk    40A8BE06409BB3E8                     
|-sdd7 ntfs    D15TB-X           2C3B1371BA233DDB                     
|-sdd5 ntfs    D15TB-VirtOS      7B724C25E321BB01                     
|-sdd1                                                                
|-sdd8 ntfs    D15TB-Overflow    C9396B4C433F2E95                     
`-sdd6 ntfs    D15TB-Wbkp        3006AFE171554C10                     
sdb                                                                   
|-sdb2 ntfs    Windows7          30D8C32ED8C2F160                     
|-sdb5 vfat    SHAREDFAT32       1CE4-145A                            /media/lub
`-sdb1 ext3    Linux             301f1cf4-7296-3d40-c14c-73d9849cfb1b /media/lub
zram3                                                                 [SWAP]
zram1                                                                 [SWAP]
loop0  squashf                                                        /rofs
sdc                                                                   
`-sdc1 vfat    MYLINUXLIVE       4002-A0EB                            /cdrom
sda                                                                   
|-sda7 ntfs    75g-Other+BIG1-400
| 908F221349890E3B                     
|-sda5 ntfs    75g-Exe           556A18883E04BEBC                     
|-sda3 ntfs    Windows7 (L:)     30D8C32ED8C2F160                     
|-sda1 ntfs    XPMAIN            8E541BF9541BE2AF                     
`-sda6 ntfs    750g-GsDataNEWInternal
  BE6CEAB06CEA629F                     /media/lub
zram2                                                                 [SWAP]
zram0                                                                 [SWAP]
lubuntu@lubuntu:~$ sudo lsblk -m
NAME     SIZE OWNER GROUP MODE
sdd      1.4T root  disk  brw-rw----
|-sdd9 486.4G root  disk  brw-rw----
|-sdd7   256G root  disk  brw-rw----
|-sdd5 132.3G root  disk  brw-rw----
|-sdd1     1K root  disk  brw-rw----
|-sdd8 305.7G root  disk  brw-rw----
`-sdd6   217G root  disk  brw-rw----
sdb    232.9G root  disk  brw-rw----
|-sdb2  75.2G root  disk  brw-rw----
|-sdb5  27.6G root  disk  brw-rw----
`-sdb1  24.8G root  disk  brw-rw----
zram3      2G root  disk  brw-rw----
zram1      2G root  disk  brw-rw----
loop0  852.1M root  disk  brw-rw----
sdc      1.9G root  disk  brw-rw----
`-sdc1   1.9G root  disk  brw-rw----
sda    698.7G root  disk  brw-rw----
|-sda7   389G root  disk  brw-rw----
|-sda5    70G root  disk  brw-rw----
|-sda3    74G root  disk  brw-rw----
|-sda1  45.6G root  disk  brw-rw----
`-sda6    80G root  disk  brw-rw----
zram2      2G root  disk  brw-rw----
zram0      2G root  disk  brw-rw----
lubuntu@lubuntu:~$ sudo parted -ls
Model: ATA WDC WD7500BPKT-7 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      8225kB  49.0GB  49.0GB  primary   ntfs
 3      91.9GB  171GB   79.5GB  primary   ntfs         boot
 4      171GB   750GB   579GB   extended
 5      171GB   247GB   75.2GB  logical   ntfs
 6      247GB   332GB   85.9GB  logical   ntfs
 7      332GB   750GB   418GB   logical   ntfs


Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      24.7MB  26.6GB  26.6GB  primary   ext3
 2      26.6GB  107GB   80.7GB  primary   ntfs         boot
 3      132GB   161GB   29.6GB  extended               lba
 5      132GB   161GB   29.6GB  logical   fat32


Model: USB 2.0 USB Flash Drive (scsi)
Disk /dev/sdc: 2022MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2022MB  2022MB  primary  fat32        boot


Model: WD Ext HDD 1021 (scsi)
Disk /dev/sdd: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
 1      3580kB  1500GB  1500GB  extended               lba
 5      3613kB  142GB   142GB   logical   ntfs         hidden
 6      142GB   375GB   233GB   logical   ntfs
 7      375GB   650GB   275GB   logical   ntfs
 8      650GB   978GB   328GB   logical   ntfs
 9      978GB   1500GB  522GB   logical   ntfs


Model: Unknown (unknown)
Disk /dev/zram3: 2088MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  2088MB  2088MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram1: 2088MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  2088MB  2088MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram2: 2088MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  2088MB  2088MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram0: 2088MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  2088MB  2088MB  linux-swap(v1)



```

---

### Post by greengalaxy on 2017-03-24
I'm writing this form the LIVE version. (And i like lubuntu!)
During the failed install atempts, they began with some pages of dense text on black.   ending with:
Buffer I/O error on dev sda6
logical block 386
async page read
EH complete.
---
The "dev sda6" drive refers to a NTFS partition where I have tons of doucments.   As you see, I have lots of Partitions, on 2 internal drvies, and 1 external.   From a windows7 Easus app, I set up partitions for Linux with ext3, but the Lubuntu installer never got to its partitioner, as it froze well before that.   
I'm going to try once more, and then sleep.

---

### Post by sudodus on 2017-03-24
> **greengalaxy said:**
> Hi.  The LIVE version of Lubuntu works.    From its treminal I ran the commands and got:

```

lubuntu@lubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  9.7M  1.6G   1% /run
/dev/sdc1       1.9G  1.9G   47M  98% /cdrom
/dev/loop0      853M  853M     0 100% /rofs
aufs            7.8G  258M  7.6G   4% /
tmpfs           7.8G   53M  7.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
tmpfs           7.8G  4.0K  7.8G   1% /tmp
tmpfs           1.6G   28K  1.6G   1% /run/user/999
/dev/sdb5        28G  2.4G   26G   9% /media/lubuntu/SHAREDFAT32
/dev/sda6        81G   35G   46G  44% /media/lubuntu/750g-GsDataNEWInternal
[COLOR="#cc0000"]/dev/sdb1        25G  7.3M   24G   1% /media/lubuntu/Linux[/COLOR]
lubuntu@lubuntu:~$ sudo lsblk -f
NAME   FSTYPE  LABEL             UUID                                 MOUNTPOINT
...
sdb                                                                   
|-sdb2 ntfs    Windows7          30D8C32ED8C2F160                     
|-sdb5 vfat    SHAREDFAT32       1CE4-145A                            /media/lub
[COLOR="#cc0000"]`-sdb1 ext3    Linux             301f1cf4-7296-3d40-c14c-73d9849cfb1b /media/lub[/color]
lubuntu@lubuntu:~$ sudo lsblk -m
NAME     SIZE OWNER GROUP MODE
...
sdb    232.9G root  disk  brw-rw----
|-sdb2  75.2G root  disk  brw-rw----
|-sdb5  27.6G root  disk  brw-rw----
[COLOR="#cc0000"]`-sdb1  24.8G root  disk  brw-rw----[/color]
lubuntu@lubuntu:~$ sudo parted -ls
...
Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system  Flags
[COLOR="#cc0000"] 1      24.7MB  26.6GB  26.6GB  primary   ext3[/color]
 2      26.6GB  107GB   80.7GB  primary   ntfs         boot
 3      132GB   161GB   29.6GB  extended               lba
 5      132GB   161GB   29.6GB  logical   fat32

```

I hight-lighted the  **ext** partition, where is would be possible to install Lubuntu. The mountpoint by lsblk is truncated (probably because the output reached the end of the window), but you see the full mountpoint in the output by df. The size of the ext3 partition is 26.6 GB, which is enough. I found no swap partition. It is not necessary, but might help to have a small swap partition, maybe 1 GB, but to avoid swapping (because of wear and speed).

---

### Post by sudodus on 2017-03-24
> **greengalaxy said:**
> I'm writing this form the LIVE version. (And i like lubuntu!)
During the failed install atempts, they began with some pages of dense text on black.   ending with:
Buffer I/O error on dev sda6
logical block 386
async page read
EH complete.
---
The "dev sda6" drive refers to a NTFS partition where I have tons of doucments.   As you see, I have lots of Partitions, on 2 internal drvies, and 1 external.   From a windows7 Easus app, I set up partitions for Linux with ext3, but the Lubuntu installer never got to its partitioner, as it froze well before that.   
I'm going to try once more, and then sleep.

/dev/sda6 has the NTFS file system, and you should not install linux into a partition with that file system. Instead you should use **/dev/sdb1 with the ext3 file system** or maybe into a new partition that you create after shrinking some exisiting partition.

---

### Post by jeff666 on 2017-03-24
i think it froze before its any where near the installation process goes like this (lubuntu ubuntu ubunut server use the same software different graphics)
```

1.select language
2.select country
3.detect keyboard
4.detect hardware                       //cpu, memory controller, etc
5.load componets                       //load componts for your hardware
6.detect network hardware        
7.network config                       
8.set up accounts
9.set up time
10. detect disks
11. partitioner 
12 install system
13 set up package manager
14 install software
15 install grub
16 basically done

```
what part does it get hung up on the partitioner, the installer, or right after the detect keyboard? All are very different problems. Use the partitioner in the installer not from a windows app that will never work even if it is ext3. use windows app to shrink what ever partition so you have free space and run the installer. it won't delete your windows ntfs partitions unless you tell it too.

---

### Post by greengalaxy on 2017-03-24
Thanks much for all replies and ideas!       
 
           During the latest install attempt, from within the Live version, I, at the prompt, UNmounted all the extra partitions. Yes, it always froze LONG before getting to any partitioner or installer or ANYthing.  When it first boots it asks for language, so it got that.          
 
 Via windows, I already mostly partitioned things.         Yes, the ext3 partition labelled 'Linux' is for Linux.  But for swap, I read its best NOT to use the SSD drive, so I have a 40gig empty space on my other hdd drive I intend to use For that.  That space isn't yet formatted, as I was undecided on how much of it to use for the swap.   I have 16GB ram.  So, I guess 16GB for the swap/suspend to disc?             
 
   But the installer is supposed to have its own built in partitioner, and will give me the options to choose where and adjust sizes then.    But I never got that far, because ALL the installers I tried so far froze upon clicking the 'continue' button, at the screen that says:  'Preparing to Install Lubuntu', (same screen that asks whether I want to 'download updates +3rd party software..'.      I NEVER check the ''download updates +3rd party", (except on the very 1st attempt last week). I just click the 'continue' button, and it just freezes.                        
 
  (PS:  Yes, I already stated that sda6 was NTFS full of all my documents, so of course I'm not installing over all my work.  I never got to the point of begin able to choose a partition.  I was just asking if the "Buffer I/O error" was relevant.   Probably not, because the same thing showed when booting live, and the live version worked wonderfully. ) 
 Thanks for any help

---

### Post by sudodus on 2017-03-25
Use at least as much swap as RAM in the same units. RAM is usually measured in GiB (gibibytes, base 2).

```
$ bc
bc 1.06.95
Copyright 1991-1994, 1997, 1998, 2000, 2004, 2006 Free Software Foundation, Inc.
This is free software with ABSOLUTELY NO WARRANTY.
For details type `warranty'. 
scale=3
16*2^30/10^9
17.179
```

In other words, 16 GiB ~ 17.179 GB.
 
So I would recommend 18 GB swap (to provide a small margin) for hibernation. If you do not intend to hibernate, it would probably be enough with 2 GB swap unless you know that you will use programs that need a lot of RAM.

-o-

I don't know why your computer freezes, but it might help with some boot option. The following link and links from it might help you use some boot option.

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

---

### Post by jeff666 on 2017-03-25
ok so live works but when you go to the installer you choose your language and it crashes for both Ubuntu and lubuntu .
a few more ideas for you

1.Are you using rufus to make the live usb? should work but you could try (if you have another usb stick) booting up the live version downloading another image and 'dd if=<path to image> of=/dev/sde' (e is a example but do not go like this "of=/dev/sde1" that is incorrect.

2.i know you want lubuntu as a end result but mabey see if one of these work debain, fedora or centOS. 

3.Reason i wanted you to give ubuntu server a try is because it is not graphical and very simplified installer it might give some sort of further insight into what part is failing.

4.I did have some trouble once with one of my samsung ssds(850 evo)  i had to wipe it to get it to work. Windows has a very decent tool for backup from elevated command prompt 'wbadmin' (which you will take a snapshot of your system, if your messing around with linux should have that anyway, won't want to loose those documents). Once you have that snap shot (make sure you also have windows usb installer as well) wipe your disk with live linux, install windows with a regular partition scheme and install lubuntu (with free space (use its partitioner) no previously defined partitions you made with windows, JUST LEAVE FREE SPACE)

5. did you change anything in the uefi (bios) reset it all try again

sorry if no of that works its beyond me at the moment hopefully there is some take away from that tho. also not that i mean to conflict your advice sudodus (im sure you have your reasons and defiantly have your experience) but why 18gb of swap thats soo much ive never come close i have 16gb ram and i have no swap never had a problem running youtube, 6 tabs, 5 vms, openbox, conky, terminal all at once. I would say no swap or 2-8gb at most with swappiness at like 10. Not at all trying to offend every system/person is different my macbook had 4gb ram and 4 gbs swap but ran hot so i reduce it to .5gb ram and 12gb swap (swappiness 70) it is now much happier.

---

### Post by greengalaxy on 2017-03-25
Thanks for not giving up on me!  
  I have very old USB pendrives, so I'm going to order some new better ones from Amazon today. But it failed from the DVD also, so that's probably not the problem. 
 
 @jeff666:  INTERESTING what you wrote about your Samsung SDD problem!!!  I have the EXACT same one:  Samsung 850 EVO 250 GB M.2 SSD.  Maybe that's the problem!  I'd hate to have to wipe the disk, but might.   I have plenty of backups.     
 
 BUT I always read that you should install Windows first, then Linux, because linux grub will see windows for the multiboot switching.   Whereas if I install windows after Linux, then Windows removes the Grub loader.   It's possible to fix that, but I don't relish trying.   
 
 I could wipe the drive, install Linux, and then use my drive-imager (ShadowProtect ) to put my image of Windows7 back on its partition.  But I'm not sure if the drive-imager can take care of the MBR (I'm legacy) for Windows.   And if Grub could then 'see' Windows.   Could be messy. 
 
 (Actually after a few months, I'll mostly use Windows from Linux through VirtualBox, which works so very well.  But will need a true install for some MS Visual Studio code compilings. )   
 
 So I think I'll order a new SSD drive.  Can anyone suggst their experience on this?  What brands work best for multiboot installs? 
 
 Good explanation on why the Ubuntu server is worth trying.  I'll give it a shot, but I'm also going to try Mint, Zorin, Manjaro... (Back in the day, I used Slackware.) 
 
 
 @sudodus, et al:  Since it worked so well in LIVE version, on old USBstick, I'm thinking:  Can I use a blank SDD, put it in my USB3 drive ENCLOSURE, and put a live version on it?  That would be much faster and cheaper than running it from USB thumb drives.   It would be the same speed as a real install.    And with persistance, it would be a portable OS.    
 
 There are MANY multiboot thumb drive creators, that have persistance.  I tried 'LinuxLive USB Creator', and Rufus.   Would any of these work to do the same on an external SSD?   Recommendations?  
 
 Sudodus, with your expertise on portable OS, you have tried this? 
 
 -Thanks to all.

---

### Post by sudodus on 2017-03-26
> **greengalaxy said:**
> ...

 @sudodus, et al:  Since it worked so well in LIVE version, on old USBstick, I'm thinking:  Can I use a blank SDD, put it in my USB3 drive ENCLOSURE, and put a live version on it?  That would be much faster and cheaper than running it from USB thumb drives.   It would be the same speed as a real install.    And with persistance, it would be a portable OS.    
 
 There are MANY multiboot thumb drive creators, that have persistance.  I tried 'LinuxLive USB Creator', and Rufus.   Would any of these work to do the same on an external SSD?   Recommendations?  
 
 Sudodus, with your expertise on portable OS, you have tried this? 
 
 -Thanks to all.

Yes, this is possible. I have done it several times. If you use ***mkusb*** to create a persistent live drive, you need not wipe the SSD, mkusb will take care of that. And you will use the whole drive.

Persistent live drives are sensitive to damaged file systems, so please backup the **casper-rw** partition. Tools for that purpose 'backup' and 'restore' are provided with mkusb.

When using an SSD and not a simple USB pendrive, it might be a good idea to modify the casper-rw partition. Do that before you start using the persistent live system: Change the file system of the casper-rw partition to 'have journal' and it will be more reliable and easier to repair due to the journaling. It means that it will write more, which is OK with an SSD, while it might wear a simple USB flash drive until it fails.

Identify the casper-rw partition with the following command line

```
sudo lsblk -f
```
and modify with
```
sudo tune2fs -O has_journal /dev/sdx5  # where x is the drive letter found by the lsblk command
```

See the following links,

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

If you must start from Windows, you can use a cloning tool and install from a compressed image file in one or two steps according to the following links,

[wiki.ubuntu.com/Win32DiskImager/compressed-image_2_USB-or-SD](https://wiki.ubuntu.com/Win32DiskImager/compressed-image_2_USB-or-SD)
[Compressed image file with a persistent live system](https://help.ubuntu.com/community/mkusb/persistent#Compressed_image_file_with_a_persistent_live_system)
[Small 9w systems with guidus alias mkusb-dus and gparted installed](https://help.ubuntu.com/community/mkusb/persistent#Small_9w_systems_with_guidus_alias_mkusb-dus_and_gparted_installed)

---

