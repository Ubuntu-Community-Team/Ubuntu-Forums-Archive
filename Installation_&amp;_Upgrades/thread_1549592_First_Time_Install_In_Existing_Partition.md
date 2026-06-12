---
title: "First Time Install In Existing Partition"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by Scottar on 2010-08-10
[SIZE=2]Hi, I would like to get some help on installing Ubuntu 10.04? to my hard drive which has Windows XP Pro installed- SP-3. I have already done a test boot off of a DVD. My computer is a Toshiba laptop with about 2 MB of ram.

I have already partitioned the drive into 6 partitions so windows won't formally accept another partition. I intend to install it on H: partition which has over 19 GB Free. Windows is on C: of course and has only 4.33 GB free. Should I empty this partition of all data?

If I understand correctly Ubuntu will create it's own separate boot partition. I'm thinking 3~5 GB. 

And if I successfully install it, how can I un-install it if I see fit to?

Thanks[/SIZE]

---

### Post by Sef on 2010-08-10
> If I understand correctly Ubuntu will create it's own separate boot partition. I'm thinking 3~5 GB. 


It should be 8 - 10 gb.


> I have already partitioned the drive into 6 partitions so windows won't formally accept another partition. I intend to install it on H: partition which has over 19 GB Free. Windows is on C: of course and has only 4.33 GB free. Should I empty this partition of all data?

Let's see how you partitioned the drive.

Applications > Accessories > Terminal

then copy and paste this command:

```
sudo fdisk -l
```

Copy and paste the results here.

---

### Post by garvinrick4 on 2010-08-10
Let Sef in post #2 help you before you start or you will be in trouble.

Put in your live CD and run in terminal like requested.

```
sudo fdisk -l
``` (small L)

Copy and paste results to this thread and you will get started on right foot.

---

### Post by Scottar on 2010-08-10
Ok, but I'm right in the middle of something and I may not get back until tomorrow night as I am using windows right now.

I have partitioned this computer so if you want details on that I can give you the details from explorer.

---

### Post by garvinrick4 on 2010-08-10
> **Scottar said:**
> Ok, but I'm right in the middle of something and I may not get back until tomorrow night as I am using windows right now.

I have partitioned this computer so if you want details on that I can give you the details from explorer. Windows partitions would be in letters and Linux shows sda1, sda2, sda3 and so on instead of C, D, E, F and so on. When you install Linux you will use the sda #'s so give us the results of:
in linux install CD using Try ubuntu.

```
sudo fdisk -l
```

---

### Post by oldfred on 2010-08-10
I typically  recommend this:

1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all (that you want to allocate) but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

If you have a NTFS shared data partition for data from both windows & Ubuntu you can use a smaller  /home. You do not need to have separate system partitions on a standard desktop install so no /boot unless you have a real old system with BIOS limits on booting larger drives.


Full Disk install Lucid Graphical
 [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

Dual Boot Win7 & Ubuntu
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)

[]("http://www.psychocats.net/ubuntu/installing")

---

### Post by Scottar on 2010-08-11
> **Sef said:**
> It should be 8 - 10 gb.




Let's see how you partitioned the drive.

Applications > Accessories > Terminal

then copy and paste this command:

```
sudo fdisk -l
```Copy and paste the results here.


Here are the results:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk identifier: 0xb97eb96e

Device Boot           Start       End      Blocks    Id          System
/dev/sda1               1         192     1536000    27       Unknown Partition 1 does not end on cylinder boundary.
/dev/sda2   *         193        2756    20595330    7      HPFS/NTFS
/dev/sda3            2757       19456   134142750    f      W95 Ext'd (LBA)
/dev/sda5            2757        3393     5116671    7      HPFS/NTFS
/dev/sda6            3394        4668    10241406    7      HPFS/NTFS
/dev/sda7            4669       11680    56323858+   7      HPFS/NTFS
/dev/sda8           11681       16779    40957686    7      HPFS/NTFS
/dev/sda9           16780       19456    21502971    7      HPFS/NTFS

ubuntu@ubuntu:~$

I forgot to tell you that I downloaded the 64 bit version Ubuntu while I'm using the 32 bit version of Windows XP- Pro so the drive may not be properly formated for Ubuntu 64 AMD, not sure

---

### Post by oldfred on 2010-08-11
Linux cannot use NTFS for its system but can read it for data. So you will have to reformat your partitions for / (root) & /home. It may be easier to just delete and recreate with gparted from the liveCD and use manual install or jsut install and from the installer reformat.

---

### Post by Scottar on 2010-08-11
> **oldfred said:**
> Linux cannot use NTFS for its system but can read it for data. So you will have to reformat your partitions for / (root) & /home. It may be easier to just delete and recreate with gparted from the liveCD and use manual install or jsut install and from the installer reformat.

[SIZE=2]So Oldfred;

You are saying I should delete one of the Partitions that  have 30 GB or more and create that space as a Ubuntu partition using [/SIZE][SIZE=2]gparted ? 

So that would create a boot partition for  ubuntu?

Could it access data from the NTFS partitions?
[/SIZE][SIZE=2]
Thanks[/SIZE]

---

### Post by oldfred on 2010-08-11
You do not need a /boot partition but a / (root) partition. 
Servers, RAID configurations, encrypted partitions and old systems that can only boot from the beginning of a hard drive may need /boot, otherwise it is just part of root.

Yes you will have to reformat at least one partition. You also should create a swap partition of 2GB or the size of RAM if you want to hibernate. Ubuntu reads & writes NTFS & FAT just fine. We still have a shared partition from when we used windows a lot. I do not recommend writing into system partitions from foreign systems unless you have to for repairs. I read from my windows but when in windows save data to the shared partition and in Ubuntu anything I might want in windows I write into the shared. The windows system partition sometimes does not like a lot of changes from others.

Windows cannot create partitions for Ubuntu as it does not know about Linux formats.

---

### Post by Scottar on 2010-08-12
[SIZE=3]Oldfred;

Your not very clear about the use of gparted  utility. Is this part of the Ubuntu live CD package?
 Does it directly  overwrite and format a targeted partition created by windows?
Is it's use  self explanatory?
Can the swap partition be an existing temp partition?
It  would be nice to have a link to it's exact use. Not much I can find in the docs section.
[/SIZE]

---

### Post by oldfred on 2010-08-12
Some links:

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by Scottar on 2010-08-14
[SIZE=3]Oldfred;

Thanks for the help.

Nice references.  

[URL="http://www.dedoimedo.com/computers/gparted.html"]http://www.dedoimedo.com/computers/gparted.html
[/URL]was  really good.

[URL="http://guvnr.com/pc/ubuntu-partition-planning/"]http://guvnr.com/pc/ubuntu-partition-planning/
[/URL]was  pretty good also

I recommend the above links for anyone wanting to install Ubuntu for the first time or even modify it.

I have yet to attempt it, have some loose ends in windows to do first.
[/SIZE]

---

