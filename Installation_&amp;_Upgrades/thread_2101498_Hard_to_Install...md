---
title: "Hard to Install.."
date: 2013-01-04
forum: Installation &amp; Upgrades
---

### Post by Jacobsen0 on 2013-01-04
I want to make a dual boot with win7, but...

My computer spec:

Geforce 580 GTX
Intel I7 2600k
16gb 1600mhz ram
GigaByte GA-Z68P-DS3
OCZ Vertex3 SSD 120gb
WD HDD 1tb
Dual Samsung 27" Monitors

1)
Because the nouveau driver cant handle my grafics card it crashes/freezes the installer, the only way I can start installing is by using the advanced installer with 'nomodeset', that works until it gets stuck forever on "configuring hardware".. I have tried using "download updates while installing" and "install this third-party software" but still no good.. [insert sad panda face here]


2)
Before I started trying to install I made 40gb free space for ubuntu on my SSD and some on my HDD, but..

When I did the "fail try" installing ubuntu it did make the partitions, 
but when I check in win7 disk management I can see it made all the partitions on my HDD's free space.. not even touching the free space on my SSD alongside my win7. 
 
When I did the partition options in ubuntu I had "alongside win7" "Replace Win7" or "Something else" so I choose alongside win7 to get my dual boot..  
so why did it choose the HDD when there is room on my main SSD disk? (as set in the bios) and of cause I want it on my SSD  :)


3)
I guess theres no easy option for me to install it on this computer.. :shock:  
I have been google'ing how to partition linux.. and there is soooo many different ways to do it 
and I am not an expert in linux(yet) 
 
So far what I have found out is that I want my /home on my HDD and the rest on the SSD I need to make a swap + Extended partition and then one for the rest of the system. 
So 3 partitions on my SSD and 1 on my HDD..something like "5gb swap - 5gb extended and then system on SSD" ?

also there is no option to make a "Extended partition" in the menu..
or most likely it's just me that dont got a clue.. :confused:

What partition needs to be Primary or Logical, some says it don't matter, but why the option then ? 
What mount point should I use for each of those 3 partitions ? 
What boot loader should I install/use ? can choose between my HDD/SSD/win7 loader, and more. 
Does the Location 'beginning/end of space' matter ?

End of my issues! 
 
I really like ubuntu alot and I have it installed on a older pc, but there was no windows on it so it was very easy to install, and no driver issues at all 
 
I hope someone can help me with this so I can start using it for real   :)
Thanks for reading. 

Your Dearest:
Linux Newbie

---

### Post by houseworkshy on 2013-01-04
This is more bumping than solving but take a look at this 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)
It just might help.

---

### Post by NikTh on 2013-01-04
Hi  and Welcome 

Good description of your problems - queries , but some terminal results would help more. 
So , 
boot from the live Ubuntu media and "Try Ubuntu" do not attempt to install , then (as you reach the Desktop Environment) open a terminal (CTRL+ALT+T combo) and paste inside the commands below (one at time)
```
sudo fdisk -l 
sudo parted -l
```Post back here the results. 

 _Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [**See here how**]("http://i.stack.imgur.com/zADbK.png")

Thanks

---

### Post by darkod on 2013-01-04
1. The nomodeset should allow you to install. And you will need to add it to the boot lines on first boot. After you have booted once you can activate the nvidia driver. Try disconnecting one monitor during the install, leave only the primary monitor.

2. The auto method uses the largest unallocated space it will find and it doesn't split ubuntu between two or more disks. Also, it will install a simple two partitions setup, only / and swap. That's why it installed on only one of the disks. It will never use two disks.

3. To install with separate /home partition you need to use the manual install method (Something Else). In the manual partitioning you can control the partition sizes and their location (ssd or hdd).

Primary or logical doesn't matter for linux, the choice is there so you can choose what type of partition you want to create. A disk with msdos table can have a maximum of 4 primary partitions, or 3 primary and 1 extended which is simply a container holding all the logical partitions.

So, for example if you need only 3 partitions on a disk, you can make all of them primary. On the other hand, if you know you will need 6 partitions, you know you can't have 6 primary, so you can create first 3 as primary and then the other 3 as logical.

For ubuntu you will need only 3 partitions in total. The main system partition is called root and has the / mount point, then the /home partition you want, and the swap which has no mount point.
Make / and /home as ext4 filesystem, and swap is as swap area.

The bootloader can go on the ssd or hdd, as you wish, but it has to be on the MBR of the disk, like /dev/sda or /dev/sdb. Without any numbers, like /dev/sda5. That's a partition, not a MBR. You can install the bootloader on any of the disks, just make sure that disk is the first option to boot from in the bios so that grub2 bootloader gets booted. Windows bootloader can't boot linux.

The begin/end when creating partitions is a choice where in the unallocated space to be created, again, so you have the choice to plan your disk layout better. For example, you have 100GB unallocated space and you are creating 20GB partition. It is asking you whether you want to create it in the first or last 20GB out of those 100GB.

There is no creating extended partition in linux, you make logical partitions and all of them need to be next to each other on the disk. The extended partition container is created automatically around them, so they are all part of it.

That should be enough to get you going. :)

If you have more question, feel free to ask.

---

### Post by Jacobsen0 on 2013-01-05
Now I know how to partition my computer but the problem seems to be how/when I can install the nvidia driver before the installation automatically gets to the "configuring hardware" part...

In the advanced installer I can use the 'modes' option "Use driver from update disk" but I don't have the motherboard cd with drivers.. and I tried burning a cd with the driver you get from nvidia webpage, that didn't work. 
 
If I try to get the nvidia driver via the terminal before I get to the partitioning part, 
it can download it(apt-get) but fails and gives me allot of errors shown in the terminal.. 
 
After I have done the partitioning I don't get any options/chance to install drivers because it just starts installing until it hits "configuring hardware" and using the terminal to get the drivers just gives me the same errors as before partitioning. I only get the "where you from" "keyboard layout" "who are you" option 
 
I have also tried "Try ubuntu without installing" then I can install the driver(apt-get) without any errors in the desktop terminal, but when I choose to install after.. it still gets stuck on "configuring hardware" 
 
with my current knowledge about linux.. 
The way i install nvidia drivers on my old PC was with: 
 
sudo apt-get install nvidia-current 
sudo reboot 
 
in what way should i install the driver on this PC ?

just my disk info:
```
disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x361c47bf

   Device Boot    Start          End       Blocks    Id    System
/dev/sda1   *      2048       206847       102400     7    HPFS/NTFS/exFAT
/dev/sda2        206848   1722357759    861075456     7    HPFS/NTFS/exFAT

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x36c47b7

   Device Boot    Start          End       Blocks    Id    System
/dev/sdb1          2048    151205887     75601920     7    HPFS/NTFS/exFAT
``````
Model: ATA ST31000524AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system   Flags
 1      1049kb  106MB  105MB  Primary  ntfs          boot
 2      106MB   882GB  882GB  Primary  ntfs          


Model: ATA OCZ-VERTEX3 (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system   Flags
 1      1049kb  77.4GB  77.4GB  primary  ntfs

Error: Can't have a partition outside the disk!
```

---

### Post by darkod on 2013-01-05
Usually the nvidia driver doesn't stop you at configuring hardware. I am not sure this is your problem.

Using the nomodeset to load the live session, and then starting the install in most cases finishes the installation correctly. Then on first reboot you need to use nomodeset again to load the installed OS and activate the driver.

You don't need to worry about installing a nvidia driver during the install.

There might be another issue stopping it. You say you can load the live mode correctly, right?

---

### Post by NikTh on 2013-01-05
> **darkod said:**
> 
Using the nomodeset to load the live session, and then starting the install in most cases finishes the installation correctly.  
IF not , you can try the alternate install .iso (available for 12.04 LTS)  can be found here : [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

Thanks

---

