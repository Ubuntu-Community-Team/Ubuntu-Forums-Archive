---
title: "Question : How to Install LVM Partitions on top of RAID 1, not software RAID?"
date: 2012-09-30
forum: Installation &amp; Upgrades
---

### Post by moiyd on 2012-09-30
Hello,

I'm new here in this amazing forum, in fact I'm newly shifting to the amazing O.S. Ubuntu ;)

I trying to quit MS Technology as I can, Linux ROCKS :D

So, excuse me if you thought my question is old or has predictable answer.

My question is 

How can I install LVM Partitions on TOP of RAID 1 using XUbuntu 12 ?

I saw an amazing thread here 
[http://ubuntuforums.org/showthread.php?t=1782296](http://ubuntuforums.org/showthread.php?t=1782296)

It's perfect but still I don't know how to do it on top of RAID 1 !!

Not software RAID !!!.

I have 2 HDD, I made'em RAID 1, and I need to apply LVM on top of them.


Thanks in advance, much appreciated.

BR, Moiyd

---

### Post by coffeecat on 2012-09-30
Hi - and welcome to the forum.

You posted in Tutorials and Tips which is only for people posting tutorials and is moderated. I've moved this to Installation & Upgrades for you.

---

### Post by darkod on 2012-09-30
If you want to install with LVM you need to use the Alternate CD (image). That one has support for LVM and RAID.

If you are not dual booting with windows, it might be actually better to use software raid, but you can use hardware raid or fakeraid if you wish to.

The alternate installer should recognize the existing raid array, and as already said it offers support to install LVM.

All Xubuntu 12.04.1 LTS images are here:
[http://cdimage.ubuntu.com/xubuntu/releases/12.04.1/release/](http://cdimage.ubuntu.com/xubuntu/releases/12.04.1/release/)

---

### Post by moiyd on 2012-10-01
Coffeecat sorry !! honest mistake .. thanks

darkod, thanks for replay

Actually I have a machine supports both LVM and RAID

as I mentioned earlier, I have two HDDs, I made them RAID 1 from the BIOS ( RAID Controller Utility ).

So, I have already two HDDs functioning well and mirroring perfectly.

2 TB


so, I followed the mentioned instructions as written in this post
[http://ubuntuforums.org/showthread.php?t=1782296](http://ubuntuforums.org/showthread.php?t=1782296)

except, this post explain how to Install LVM Partition on regular HDD drives ( NOT RAIDED HDDs )

When I putted the booting CD and browsed the HDD list using this command
sudo fdisk -l

there is 3 HDDs available or lets say spaces to use ;)

/dev/sda I suppose this is HDD 1
/dev/sdb I suppose this is HDD 2
/dev/mapper/isw_cffeiahdid_Volume0 ( Which is the result of the RAID 1 I suppose )

the great question is, Which part of these little 3 spaces I shall use to Install my LVM partitions, and remember I have to install them on top of RAID

shall I use (sda) and it well duplicates itself automatically ? is boot sector ( if the space duplicated to sdb ) going to be alright !! ?

or shall I use this mapper partition ( that created because of RAID 1 ) ?


Please help me out with this thing, I still a stranger in Ubuntu world :(

much appreciated.

BR, Moiyd

---

### Post by darkod on 2012-10-01
You need to use the /dev/mapper/... device because that is the array. You install with LVM considering the /dev/mapper/ as a single disk device, it's the same. You simply use a raid array in place of a single disk.

So, the the /dev/mapper/ will be the physical device for the LVM.

---

### Post by moiyd on 2012-10-01
thanks for replay me

but, what is the device boot loader should be ?

regards

---

### Post by darkod on 2012-10-01
The MBR of the array, which would be something like /dev/mapper/blah_blah_Volume0

The partitions of the array would usually end in Volume0p1, Volume0p2, etc, and the MBR in that case would be only Volume0 (without any identificator for a partition).

---

### Post by moiyd on 2012-10-01
Hola Darkod

Mochas Gracias

I still wonder, is it possible to do the following :

according to my adviser, he wants me to do the whole setting in this way,


Make 500 MB for boot and EXT4 ( out of RAID 1 and out of LVM )

the rest of the RAIDed HDDs make it LVMs

12G for SWAP ( LVM )
24G for Root and it's XFS file system ( LVM ) 
20G for Home and it's XFS file system ( LVM ) 
20G for temp and it's XFS file system ( LVM ) 
20G for var and it's XFS file system ( LVM ) 

so, basically How can I extract 500MB from the HDD 1 before it's mirrored with HDD 2 and make it dedicated for /boot ( you know according to his command, out of RAID and LVM ) ?

I really do appreciate your help
Best Regards, Moiyd

---

### Post by darkod on 2012-10-01
I don't think you can do that with bios raid / hardware raid. hardware raid works on disk level, you specify the disks as members of the array and you can't leave partitions out of it.

Software raid can work on both disk or partition level, so you can easily first create 500MB ext4 partition on both disks (for simmetry, you don't need to use the 500MB partition on sdb if you don't want to), and then create a partition marked as raid from the rest of both disks. You create the raid1 array from partitions sda2 and sdb2 for example, and that way sda1 and sdb1 are left outside the array.

But I am not aware of a way to do that with hardware raid.

Also note that making /boot only on one disk beats the purpose of raid1 because in raid1 if one disk fails the system needs to keep going. If you have /boot outside the array and only on one disk, if that disk fails the system will stop working because /boot was only there and doesn't exist on the other disk.

Maybe he is confused because earlier you needed a /boot partition outside the LVM so it can work but these days with the latest ubuntu releases you can work with LVM without the separate /boot outside it.

If he insists that only part of the disk is a member of the raid array, you can't use hardware raid.

---

### Post by moiyd on 2012-10-01
I would like to thank you for your support. You really made the image clear a little bit, I was confused.

Now maybe for last procedure, here what I suppose to do:

RAID 1 it Harwarely ;)

then

fist, lunch the new space ( the Mapper space ) generated because of RAID 1

sudo fdisk /dev/isw_cffeiahdid_Volume0

and then cut a little piece of space ( 500 MB ) that would cause 
sda1 on the Real HDD Partition and,
/dev/isw_cffeiahdid_Volume0p1 on the RAIDed Partition.

of course it will automatically generate sdb1 with the same space on the mirror HDD.

and the rest of the space I shall create it and that would be
/dev/isw_cffeiahdid_Volume0p2

Am I doing great till this far ?!

now apply LVM on this new little weird volume
/dev/isw_cffeiahdid_Volume0p2

is it partitioned already now ? or there is something I shall do to complete the Installation

I shall put /boot for this 500MB which is should be Physical Partition
and LVMs on the other Logical Partition


Ohhh, it's confusing, my god !

your replay is highly appreciated

BR, Moiyd

---

### Post by moiyd on 2012-10-01
Gentlemen, any suggestions ?

regards

---

### Post by darkod on 2012-10-01
As I said, using LVM with 12.04 you don't need a separate /boot outside the LVM. But if you prefer, you can make one.

In that case, when you do the manual partitioning using the Alternate installer, first make a 500MB ext4 partition on the raid device. Set the boot flag on it and the mount point /boot.

Then from the rest of the raid device make a big partition with type LVM. After you create it, on the top go to Configure LVM which will ask you to create at least one Volume Group, and you should create the Logical Volumes you want (that you listed earlier).

After that in the disk layout they will show as devices. Select them one by one, and choose which filesystem to be used and the mount point.

That's it.

Note that you are creating the partitions on the raid device, don't mention sda and sdb any more, they don't exist as far as you are concerned. Once you configure raid you need to work with the array. If you try to work with the disks you will probably break the array.

---

### Post by moiyd on 2012-10-01
thanks for replay Darkod

I will try on that one.

regards

---

