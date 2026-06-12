---
title: "Shared linux swap/windows hibernate parition in dual boot system"
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by nikosd on 2013-11-30
Hello all,

I am about to set up for dual boot, win7/ubuntu 13.10, or mint. Windows is pre installed. Setting up a windows virtual machine is not an option because HP does *not* provide warranty coverage if you remove the pre installed windows, which includes their "proprietary" diagnostic software (I already had to wipe out linux once to put windows back and get my dead battery replaced -one month of setting up ubuntu down the drain). 

I am wondering if I can use the existing windows hibernation partition also as a swap partition for linux to save myself a few GB on my solid state drive (win7 will occupy 20 GB + 15 GB for recovery already!) 

Current disk partitioning looks like:
System- 199 MB  (primary NTFS)
C: 100 GB (primary NTFS)
D: 15 GB, Recovery (primary NTFS)
E: 101 MB, HP_TOOLS (Logical FAT32)
 Hibernation 4GB (no file system listed)

If that is not an option, I will just remove the windows hibernation and not allow the poor sucker to hibernate from windows. 

Thanks, 

Nikos

---

### Post by tgalati4 on 2013-11-30
The swap partitions are not compatible, so you won't be saving any space.  You could set up using a swap file instead of a swap partition in either Ubuntu or Windows.  Not sure about Windows, but in linux the swap partition needs to be just slightly larger than RAM for successful hibernation.

---

### Post by oldfred on 2013-11-30
Is this an Ultrabook with the small SSD?
I have seen users just install Ubuntu to hard drive and turn the Intel SRT back on, to install Ubuntu's / (root) to SSD and never use the SRT, and some have larger SSD and the SRT seems to only use part so they were able to do both.
        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

---

### Post by nikosd on 2013-12-14
[SIZE=5]Hi  guys, 

sorry it took a while.[SIZE=5] [/SIZE]The  issue is not fully resolved, but I can tell you what I tried: Resize  the windows hibernate partition from within windows (I resized it to  minimum allowed of 512 MB). Then use gparted or equivalent to manage[SIZE=5] partitions, and proceed with linux install.

[SIZE=5]Windows would not allow me[SIZE=5] to resize the n[SIZE=5]tfs parittion to below 75 GB. I only have 126 GB on this ultrabook [SIZE=5]SSD, so I decided windows had to go. I left the [SIZE=5]HP[SIZE=5]_[/SIZE]TOOL[SIZE=5]S F[SIZE=5]AT 32 [SIZE=5]partition in place, and will try to set up a virtual machine to use it[SIZE=5]. Hopefully all [SIZE=5]I [SIZE=5]need to diagno[SIZE=5]se hard[SIZE=5]ware problems to[SIZE=5] [SIZE=5]HP's satisfaction is in there, but it's a far[SIZE=5] shot..[/SIZE].[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE] 

Cu[SIZE=5]rre[SIZE=5]ntly the drive is par[SIZE=5]ti[SIZE=5]tioned as 
/ 10 GB, ext4
/home, 112 GB, ext 3
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]HP[SIZE=5]_[/SIZE]TOOLS,  101 [SIZE=5]MB, FAT32[/SIZE]
swap[SIZE=5], 4 GB, swap

mint works fine with this, I will [SIZE=5]update this thread again when/if I get HP_TOOLS working from a windo[SIZE=5]ws [/SIZE]virtua[SIZE=5]l machine. 

[SIZE=5]I am marking this as closed for now.[/SIZE]
[/SIZE][/SIZE][/SIZE]
[/SIZE][/SIZE]

---

