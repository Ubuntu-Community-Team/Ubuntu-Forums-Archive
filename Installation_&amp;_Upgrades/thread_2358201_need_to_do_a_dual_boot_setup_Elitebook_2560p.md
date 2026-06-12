---
title: "need to do a dual boot setup Elitebook 2560p"
date: 2017-04-10
forum: Installation &amp; Upgrades
---

### Post by yonnie on 2017-04-10
haven't done this in 10 years, but now I need to replace with newer stuff.  I want to install Kubuntu yet keep the win10 operable and be able to choose which OS at boot time.  
Where can I find a howto that walks me through dual-booting setup with this newer hardware?

---

### Post by oldfred on 2017-04-10
HP is not particularly friendly with UEFI dual boot. But yours may be BIOS/CSM boot if Windows 7.
Post this from terminal in live installer.

sudo parted -l

If MBR, then Windows has to boot in BIOS mode. If gpt then Windows has to boot in UEFI boot mode.
And then you want Ubuntu in same boot mode as Windows.
If MBR, same instructions as used for last 35 years (ok Ubuntu has not been around that long, but BIOS/MBR has). You have the 4 primary partition limit and have to convert one to an extended and install Ubuntu in Logical partitions.
If gpt see link below in my signature as a starting point.

---

### Post by yonnie on 2017-04-10
kubuntu@kubuntu:~$ sudo parted -L
parted: invalid option -- 'L'
Usage: parted [-hlmsv] [-a<align>] [DEVICE [COMMAND [PARAMETERS]]...]
kubuntu@kubuntu:~$
Sorry, Couldn't read the small print.... using win10, not w7

kubuntu@kubuntu:~$ sudo parted -L
parted: invalid option -- 'L'
Usage: parted [-hlmsv] [-a<align>] [DEVICE [COMMAND [PARAMETERS]]...]
kubuntu@kubuntu:~$ sudo parted -l
Model: ATA MTFDDAK128MAM-1J (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  368MB  367MB   primary  ntfs         boot
 2      368MB   112GB  112GB   primary  ntfs
 3      112GB   128GB  15.7GB  primary  ntfs         diag


Model: SanDisk Cruzer Facet (scsi)
Disk /dev/sdb: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  8004MB  8004MB  primary  fat32        boot


kubuntu@kubuntu:~$

---

### Post by yonnie on 2017-04-10
1. Which way do I shrink the partition #2 so I can insert a Kubuntu partition?
2. Is there an installer that will do this automagically?
3. How much room does W10 require to function?

---

### Post by yancek on 2017-04-10
Use windows Disk Management tool to shrink partition 2, the largest partition and after doing that reboot windows and run chkdsk from a command prompt.  Before doing any of this, you should probably run the disk defragment tool in windows.  After doing this, you will have unallocated space on which to install Kubuntu.  25Gb should be enough.  I would suggest you use the Manual install option to install as you will have more control.  I would also suggest you do an online search for dual booting windows 10 and Kubuntu/Ubuntu as there are a large number of tutorials available.  It looks like you are still using MBR and not UEFI.

---

### Post by yonnie on 2017-04-11
Would win10 run OK on a 40gb partition?  I would only be using it to run apps, never use it for pictures, vids or storing files.  But I do need to get familiar with how to navigate in it as it's so different.

---

### Post by RobGoss on 2017-04-11
I was reading that depending how and what programs you have on your system you may be able to install Windows 10, on that 40-GB partition

From my experience with Windows it has always been known to take up disk space

If you plan on keeping Windows to dated them I'm sure it will start consuming your disk space and you have problems 

Keep in mind Windows 10, is surely a better OS then Vista and Windows 7, as far as consumption is concerned and will use less...

---

### Post by yonnie on 2017-04-11
Would win10 run OK on a 40gb partition?  I would only be using it to run apps, never use it for pictures, vids or storing files.  But I do need to get familiar with how to navigate in it as it's so different.   Thanks for the shrink partition tip.  It worked and now the system boots and works.  Had a mix-up as to what to do with settings in manual mode.  Finally figured that it wanted an extra partition called swap and the first partition to be root.  Haven't done this for awhile, total guessing.  Booted right up, installed updates and even runs that other OS

---

