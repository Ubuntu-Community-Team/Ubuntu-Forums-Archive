---
title: "Is it a Logical or primary parition?"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by surati on 2013-02-10
Hi
How do I find out, with Gparted, if my partition is logic or primary?
I have for ubuntu one extended partition with (normaly)3 logical ones. After some Windows installations problem i took a look at the drivers manager and was surprised to see that ubuntu has 3 primery partitions instead of logical.
Is it a windows "apearence mistake" or maybe my mistake (this would explain my installations problem and I would just need to change from primery to logic ,when possible).
Thanks
surati

---

### Post by Cheesemill on 2013-02-10
If you can post a screenshot of gparted from Ubuntu we can tell you all you need to know.

---

### Post by offgridguy on 2013-02-10
If you have ubuntu in 3 logical partitions inside an extended
partition,  the extended is considered primary.

---

### Post by schragge on 2013-02-10
To be sure, can you please also post the output of
```

sudo fdisk -l    [color=grey]# <- it's the lowercase letter 'ell'[/color]

```

---

### Post by surati on 2013-02-10
What I would like to know is,  what is -inside- the extended partition, if these are 3 logical or 3 primary partitions....here the screenshot.

---

### Post by surati on 2013-02-10
```
255 Köpfe, 63 Sektoren/Spur, 38913 Zylinder, zusammen 625142448 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Festplattenidentifikation: 0x04f75401

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1            2048   246306815   123152384    7  HPFS/NTFS/exFAT
/dev/sdb2       246308862   378900479    66295809    5  Erweiterte
/dev/sdb3   *   378900480   624156671   122628096    7  HPFS/NTFS/exFAT
/dev/sdb5       246308864   253114367     3402752   82  Linux Swap / Solaris
/dev/sdb6       253116416   304726015    25804800   83  Linux
/dev/sdb7       304728064   378118143    36695040   83  Linux

Platte /dev/sdc: 2012 MByte, 2012217344 Byte
64 Köpfe, 46 Sektoren/Spur, 1334 Zylinder, zusammen 3930112 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Festplattenidentifikation: 0xc3072e18

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdc1   *          24     3930111     1965044    b  W95 FAT32

```

---

### Post by offgridguy on 2013-02-10
> **surati said:**
> What I would like to know is,  what is -inside- the extended partition, if these are 3 logical or 3 primary partitions....here the screenshot.
These are logical partitions within the extended.  Note the no.'s
sda 5,6 etc.   Numbers 1-4 are reserved for primary.

---

### Post by surati on 2013-02-10
Thats good to know. So I can only wonder, once again, why through windows eyes things looks different...the driver manager shows these 3 logical partitions as primery.
My problem is actualy that I cannt install windwos8 while the first driver is hidden. W8 resists to use the mbr of the first driver....

---

### Post by Morbius1 on 2013-02-10
I can't quite follow this topic. Please post the output of the following command:
```
sudo parted -l
```

---

### Post by surati on 2013-02-10
(Now I see clearly  that these are logical partitions...)

```
ubuntu@ubuntu:~$ sudo parted -l
Modell: ATA Hitachi HTS72503 (scsi)
Festplatte  /dev/sda:  320GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos

Nummer  Anfang  Ende    Größe   Typ      Dateisystem  Flags
 1      32,3kB  214MB   214MB   primary  fat16        diag
 2      214MB   10,6GB  10,4GB  primary  ntfs         versteckt
 3      10,6GB  319GB   309GB   primary  ntfs         boot


Modell: ATA Hitachi HTS72503 (scsi)
Festplatte  /dev/sdb:  320GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos

Nummer  Anfang  Ende   Größe   Typ       Dateisystem     Flags
 1      1049kB  126GB  126GB   primary   ntfs
 2      126GB   194GB  67,9GB  extended
 5      126GB   130GB  3484MB  logical   linux-swap(v1)
 6      130GB   156GB  26,4GB  logical   ext4
 7      156GB   194GB  37,6GB  logical   ext4
 3      194GB   320GB  126GB   primary   ntfs            boot


Modell: UFD 2.0 Silicon-Power2G (scsi)
Festplatte  /dev/sdc:  2012MB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos

Nummer  Anfang  Ende    Größe   Typ      Dateisystem  Flags
 1      12,3kB  2012MB  2012MB  primary  fat32        boot


ubuntu@ubuntu:~$ 

```

---

### Post by darkod on 2013-02-10
> **surati said:**
> Thats good to know. So I can only wonder, once again, why through windows eyes things looks different...the driver manager shows these 3 logical partitions as primery.
My problem is actualy that I cannt install windwos8 while the first driver is hidden. W8 resists to use the mbr of the first driver....

Windfows doesn't understand linux partitions, so it can show the logical partitions as primary in Disk Management. Ignore that and do not handle those partition with windows Disk Management.

The same happens on my PC, they are shown as primary with the correct size, which is not true.

As for installing win8, you have both your disks full with partitions, no unallocated space to use. Where do you plan to install win8?

---

### Post by Cheesemill on 2013-02-10
> **surati said:**
> What I would like to know is,  what is -inside- the extended partition, if these are 3 logical or 3 primary partitions....here the screenshot.

Partitions inside an extended partition are always logical, that is the definition of a logical partition.

You are allowed a maximum of 4 primary partitions per disc, one (and only one) of these can be an extended partition instead. Inside this extended partition you are allowed any number of logical partitions.

> **offgridguy said:**
> These are logical partitions within the extended.  Note the no.'s
sda 5,6 etc.   Numbers 1-4 are reserved for primary.
Not true. 
That is how the numbering usually ends up but there is nothing in the specifications that demands it.
You can have sda1 as an extended and 2,3,4 as logical if you want to.

---

### Post by darkod on 2013-02-10
> **Cheesemill said:**
> 
Not true. 
That is how the numbering usually ends up but there is nothing in the specifications that demands it.
You can have sda1 as an extended and 2,3,4 as logical if you want to.

I believe what he meant was that 5+ is reserved for logical, how linux will show it, not whether the physical location on the disk is second, third, etc.

Yes, the extended can have any number 1-4 but I also believe 5+ is reserved for the logicals. I still haven't seen a logical partition being /dev/sda2. Is that really possible?

---

### Post by surati on 2013-02-10
> As for installing win8, you have both your disks full with partitions,  no unallocated space to use. Where do you plan to install win8?

You are right, there is no more place...but thats because I gave up and already installed w8 on sdb3 - without hidding the first hd. Its an evaluation-version and in 3 months I will have to install it again, on the same partition. I hope untill then to find a solutoin......

---

### Post by dorruk on 2013-02-10
The Intel/PC partitioning rule is, you can have as many logical partitions as you like if they are end to end. An extended partition is the placeholder for all of your logical partitions. So when you store data on an extended, it's called a logical.

In this partitioning system, your logicals are held as one block under the name of an extended partition. For this reason, your logicals must be juxtapose so your PC can handle your logicals as one block.

Some correct partitioning examples:

```
Primary - Primary - Primary - Logical - Logical - Logical - Logical - Logical
Primary - Primary - Primary - Primary
Primary - Primary - Logical - Logical - Logical - Primary
```

Some incorrect examples:

```
Primary - Primary - Primary - Logical - Primary
Primary - Logical - Primary - Logical - Primary
```

---

### Post by darkod on 2013-02-10
> **surati said:**
> You are right, there is no more place...but thats because I gave up and already installed w8 on sdb3 - without hidding the first hd. Its an evaluation-version and in 3 months I will have to install it again, on the same partition. I hope untill then to find a solutoin......

I am not sure why win8 would complain. One reason would be if it wanted to create the small System Reserved partition and it couldn't because you already have many partitions.

Also, if installing multiple windows OS you need to be careful about the boot files because it can combine boot files on the partition where the boot flag is. I am not sure if it does that only when you have two windows OS on the same disk, or also when they are on different disks.

One thing you can try during the next win8 install is having the partition prepared in advance (don't create it from unpartitioned space with the installer). You already have the partition, you have win8 on sdb3 now. In the next install simply select Advanced options in the partitioning, format the same partition and use it as destination. I think it will install without any problems.

You shouldn't need to do any special "hiding" of the sda disk.

---

### Post by surati on 2013-02-10
> You shouldn't need to do any special "hiding" of the sda disk.     But thats my point...
I want W8 to be installd on sdb without interfering in sda, without taking over other boot loaders (w7). 
In this way I could start W7 directly from sda with the one-time-menu and grubs menu will start ubuntu & W8 from sdb. 
At the moment W8 "controls" W7´s bootloader, choosing W7 in the menu, brings the computer first to reboot instead of direct loading W7, thats anoying...
I can live with it, but I´m too curious to know what´s the problem.....and I guess it belongs to a windows forum.
Thank you anyway for the help!

---

### Post by darkod on 2013-02-10
Correct. It belongs to a windows forum. The problem is that during installation windows doesn't give you option for bootloader destination, like linux does. So you can't control where it goes. It puts it where ever it thinks it should.

That's why when installing second windows version on a separate disk it's better to disconnect the first disk.

One option is to create the partition for the second windows in advance, put a boot flag on it, and also in bios set the second disk as first booting option. Only after that start the windows installer. In that case it might put the bootloader on the second disk because it will see it's first in the boot order, and it will put its boot files on the same partition as the OS since it has the boot flag. But I'm not sure if that would work as it should or not.

That's why it's better to have manual option where to put the bootloader but with windows you don't have that.

---

### Post by surati on 2013-02-10
>  "....and also in bios set the second disk as first booting option."I didnt try it yet, sounds like a good idee!

Thanks for the Information.

(And maybe someday I would get along without windows... I hope until then ubuntu would still remain free....)

---

### Post by offgridguy on 2013-02-10
> **Cheesemill said:**
> 


Not true. 
That is how the numbering usually ends up but there is nothing in the specifications that demands it.
You can have sda1 as an extended and 2,3,4 as logical if you want to.
The info I have read disagrees with that, example.

[http://tldp.org/HOWTO/html_single/Partition/#logical](http://tldp.org/HOWTO/html_single/Partition/#logical)

2.1.3. Logical Partitions

Table 5. Logical Partitions

drive name	drive controller	drive number	partition type	partition number
/dev/hdb1	1	2	primary	1
/dev/hdb2	1	2	extended	NA
/dev/hda5	1	2	logical	2
/dev/hdb6	1	2	logical	3

	The table above illustrates a mysterious jump in the name assignments. This is due to the use of logical partitions (see Section 3.4, which always start with 5, for reasons explained later.

---

### Post by JKyleOKC on 2013-02-10
> **surati said:**
> I want W8 to be installed on sdb without interfering in sda, without taking over other boot loaders (w7).In this case, your safest option would be to physically disconnect sda when installing W8; it would then find only one drive, and would replace the boot loader on that drive. You could then reconnect sda, and use the boot-time hot key (F12 on my system but may be different on yours) to select which drive to boot from.

W8 will undoubtedly destroy the Ubuntu boot loader during the installation, but you should be able to boot from a Live CD/USB and run Boot-Repair to put it back properly.

---

### Post by offgridguy on 2013-02-11
The gparted tutorial is very helpful at explaining partitions, read it here.

[http://dedoimedo.com/computers/gparted.html](http://dedoimedo.com/computers/gparted.html)

Partitions also have another important element: they can be primary or logical. Primary partitions are just that, a total of four of which can exist on any one hard disk. To reiterate, there can be only up to four primary partitions on a hard disk. If you have three hard disks on your machine, each one can still hold up to four primary partitions.

Logical partitions have been created to overcome the inherent numerical limitation of primary partitions. One of the primary partitions can be created as the Extended partition. This partition acts as a container for logical partitions. The total number of logical partitions you can create (and use) depends on the disk type and the operating system you're using. For all practical purposes, the number is beyond the needs of any user.

As you can see, we have up to four primary partitions and a de-facto unlimited number of logical ones. Notation-wise, the primary partitions will always be the first four, logical partitions will start with number 5.

Therefore, when someone says sda5, it necessarily means we're talking about a logical partition. Similarly, any partition with a number equal or higher than 5 will always be a logical partition.

---

### Post by JKyleOKC on 2013-02-11
> **offgridguy said:**
> Therefore, when someone says sda5, it necessarily means we're talking about a logical partition. Similarly, any partition with a number equal or higher than 5 will always be a logical partition.Unless, of course, it's a machine bought new during the last year or two that uses the GPT partitioning scheme instead of the until-now-universal MBR partition table. The GPT approach allows up to 128 primary partitions and no logicals at all. Any machine that comes from the factory with Win8 installed will probably be using GPT, so take the quoted post with extreme caution.

---

### Post by offgridguy on 2013-02-11
> **JKyleOKC said:**
> Unless, of course, it's a machine bought new during the last year or two that uses the GPT partitioning scheme instead of the until-now-universal MBR partition table. The GPT approach allows up to 128 primary partitions and no logicals at all. Any machine that comes from the factory with Win8 installed will probably be using GPT, so take the quoted post with extreme caution.
Thanks for the clarification JKyleOKC,  I was actually wondering
about this. Plus the quoted tutorial is dated.

---

### Post by JKyleOKC on 2013-02-11
Here's a more up-to-date link: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by offgridguy on 2013-02-11
> **JKyleOKC said:**
> Here's a more up-to-date link: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Thanks for the link, increasingly important as more and more
threads are dealing with install and boot issues regarding the
newer UEFI mode.

---

