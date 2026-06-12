---
title: "installing ubuntu 12.04 LTS in MBR disk"
date: 2013-08-25
forum: Installation &amp; Upgrades
---

### Post by tahir2 on 2013-08-25
Hi guys I am new to Linux , I am trying was trying to install Linux in my hp laptop which have only one disk . and it is in MBR format . in Linux setup it is not showing my free space partition instead it is showing whole 750 gb free space . anyone knows how to install Ubuntu in MBR disk .. waiting for your help guys

---

### Post by Quackers on 2013-08-25
It shouldn't be a problem to install to a MBR partitioned disc. Something is wrong.
Either the installer cannot see your partitions because the partition table is damaged/corrupt. Other things could also be wrong. Have you partitioned this drive at all?
Have you tried booting from the live cd/usb and selecting "try Ubuntu"? Does it boot to a usable desktop? If so, open up gparted and see what that reports or open a terminal and run ```
sudo fdisk -l
``` and report the output please.
(The -l at the end is a lower-case L, not a 1)

---

### Post by tahir2 on 2013-08-25
yeah i am botting from my usb and the i sued live dektop .. here r the result 


sudo fdisk -l
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x68bbfca1
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   410318847   204800000    7  HPFS/NTFS/exFAT
/dev/sda3       410318848   719976447   154828800    f  W95 Ext'd (LBA)
/dev/sda4       719976448  1465145343   372584448    6  FAT16
/dev/sda5       410320896   719976447   154827776    7  HPFS/NTFS/exFAT
Disk /dev/sdb: 30.9 GB, 30943995904 bytes
32 heads, 63 sectors/track, 29978 cylinders, total 60437492 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0ea7379f
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    60435647    30217792+   7  HPFS/NTFS/exFAT

---

### Post by tahir2 on 2013-08-25
i saw in the disk utility ... its not showing any partition there

---

### Post by Quackers on 2013-08-25
As the first line of the output states you seem to have a GUID partition table not MBR. Although your partitions appear to MBR type.
Does your pc use UEFI booting? 
You can read more about GPT here
[http://en.wikipedia.org/wiki/GUID_Partition_Table]("http://en.wikipedia.org/wiki/GUID_Partition_Table")
I would read some more and familiarise with what exactly you have and what you can do with it before making any changes to your system.

---

### Post by Quackers on 2013-08-25
Has this hard drive been used in a different computer previously? Maybe in a Mac, for instance.

---

### Post by tahir2 on 2013-08-25
yeah I am using windows 8 . I am trying to dual boot it . there's separate partition for Linux . so any way to install

---

### Post by tahir2 on 2013-08-25
nope I bought this laptop few months back .. I just reinstalled the windows tried few commands from internet to change GPT to MBR to create parititions during setup

---

### Post by Quackers on 2013-08-25
STOP entering things for the moment!
We need to know how or why there is GPT data on the disk. You may need that and you may not, in which case you can destroy that GPT data with gdisk.
Obviously if you need that data for some reason you will not then be able to boot anything.
Was the laptop brand new when you bought it? Are you using UEFI to boot or BIOS?

---

### Post by tahir2 on 2013-08-25
yup the laptop was new and I am using BIOS to boot I disabled UEFI .. and there's no data right now in laptop . except windows 8 in one of the partitions . which I installed yesterday

---

### Post by Quackers on 2013-08-25
Ok, thanks. I am not familiar with UEFI booting on Windows machines and am not sure how that works.
The Ubuntu installer is looking at your hard drive and seeing both GPT data and MBR data so stops at that point in order to stop you from making any changes that may damage your system.
You could run the Ubuntu live cd/usb and select try Ubuntu then install gdisk and follow the instructions below for destroying the GPT data but follow them all - including the answering "n" to the MBR wipe.
[http://www.rodsbooks.com/gdisk/wipegpt.html]("http://www.rodsbooks.com/gdisk/wipegpt.html")

But beware!!!!
If you destroy that GPT data Windows may not boot in UEFI mode again (or even boot at all as I understand it). 

My own feeling is that you could destroy the GPT data and everything would be fine but I'm not the person who would have to re-install everything if it doesn't work.
The decision is yours.

Maybe you should wait and see if anybody else can give more information on this before you do anything.

---

### Post by tahir2 on 2013-08-25
yeah lets see.. by the way I followed this procedure before installing windows 8 . 
[http://support.microsoft.com/kb/282793](http://support.microsoft.com/kb/282793)

but I don't understand even there's a part of hard disk which is still in GPT the Linux setup should see it as free/used space . its showing whole 750 gb disk as free space

---

### Post by Quackers on 2013-08-25
Right, I understand more now. You've actually changed a GPT disc to a MBR disc.
However, it seems that the method you used has left some stray GPT data on the disc which needs to be deleted. The method shown above will do that and everything should be fine. DO NOT answer "y" to the MBR wipe section or all will be lost!

The reason the Ubuntu installer refuses to see your partitions is because both GPT data and MBR data is present on your disc. So, in an effort to stop you doing damage to your system the installer refuses to allow you to change anything.

---

### Post by tahir2 on 2013-08-25
got this error ..

gdisk /dev/sdc
The program 'gdisk' is currently not installed.  You can install it by typing:
sudo apt-get install gdisk
You will have to enable the component called 'universe'

sudo apt-get install gdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gdisk

---

### Post by Quackers on 2013-08-25
duplicate post

---

### Post by Quackers on 2013-08-25
You will have to enable the 'universe' repository to get the package. Go to software & updates (or software sources) and tick the box where the description ends with universe.
Then in the terminal run ```
sudo apt-get update
```

Once installed you don't want to run gdisk on /dev/sdc like you did above!
The disc you want to run it on is /dev/sda so in the terminal you would run ```
gdisk /dev/sda
```

---

### Post by tahir2 on 2013-08-25
yeah i installed the its from synaptic . here's the result 

first i checked my partition 

sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x68bbfca1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   410318847   204800000    7  HPFS/NTFS/exFAT
/dev/sda3       410318848   719976447   154828800    f  W95 Ext'd (LBA)
/dev/sda4       719976448  1465145343   372584448    6  FAT16
/dev/sda5       410320896   719976447   154827776    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 30.9 GB, 30943995904 bytes
32 heads, 63 sectors/track, 29978 cylinders, total 60437492 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0ea7379f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    60435647    30217792+   7  HPFS/NTFS/exFAT

then ,

sudo gdisk /dev/sda1
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by typing 'q' if
you don't want to convert your MBR partitions to GPT format!
***************************************************************

Exact type match not found for type code 7200; assigning type code for
'Linux filesystem'
Exact type match not found for type code 6C00; assigning type code for
'Linux filesystem'

Warning! Secondary partition table overlaps the last partition by
3888964533 blocks!
You will need to delete this partition or resize it in another utility.

this result is same for all except sda 4 which is 

sudo gdisk /dev/sda4
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.

---

### Post by tahir2 on 2013-08-25
can't find any gpt

---

### Post by Quackers on 2013-08-25
You've run gdisk on a partition not the disc!!!!
sudo gdisk /dev/sda  NOT  sudo gdisk /dev/sda1

---

### Post by tahir2 on 2013-08-25
oh yeah sorry my mistake .. thanks alot it worked its been whole i was trying to solve this .. marking it as solved .. again thanks alot mate ...

---

### Post by Quackers on 2013-08-25
Glad to hear that - well done!
I hope gdisk didn't damage any of your partitions. I don't think so. 
Enjoy Ubuntu!

---

