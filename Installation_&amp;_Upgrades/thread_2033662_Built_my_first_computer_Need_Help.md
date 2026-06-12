---
title: "Built my first computer Need Help"
date: 2012-07-26
forum: Installation &amp; Upgrades
---

### Post by homesplat on 2012-07-26
Hello,

I just built my first computer and I wanted to install windows and Linux on it.  Right now there are 0 OS's installed on it.  I want to install Ubuntu 64bit now so I can use this beast but I want to install Windows later for gaming.

I have never partitioned a hard drive before and I have some questions.  I was reading the post about 'Basic Partitioning Knowledge' and it said that Windows can only be installed as a primary partition and not a logical partition.  So I'm guessing this means I have to partition Ubuntu as SDB2?

Also, my computer is using an SSD and I have heard that there are programs I can install to move the tiny write cycle that OS's perform on startup to the HDD in my computer to make my SSD last longer.  Does anyone know if this is true?  Or how to do this?

Thanks for reading this and any help is greatly appreciated.

Here are the specs on my computer:
AMD Phenom II X4 975
128 GB OCZ SSD
500 GB WD HDD
16 GB DDR3 1833 G.Skill RAM

Hopefully that's all the info that is needed.

Again thank you!

---

### Post by darkod on 2012-07-26
What you can do, is decide how big you want the windows partition, boot the ubuntu cd in live mode and using Gparted create a primary ntfs partition of that size at the start of the ssd.

After that you can use the rest of the ssd for ubuntu as you want. If you are setting up a swap partition it should be on the hdd, not on the ssd.

---

### Post by homesplat on 2012-07-28
How do you decide what portion to dedicate to each OS?  What is the purpose of dedicating a different size to each?  And what is the difference between a swap and a logical partition?

---

### Post by 2F4U on 2012-07-28
> **homesplat said:**
> How do you decide what portion to dedicate to each OS?  What is the purpose of dedicating a different size to each?  And what is the difference between a swap and a logical partition?

It is mostly up to you to decide how much space you dedicate to each operating system, since it depends on how you intend to use it and how much software you are going to install. You should be fine dividing the SSD equally between Windows and Ubuntu.

---

### Post by oldfred on 2012-07-28
Is this a new UEFI/gpt system or older BIOS/mbr system? If new UEFI it complicates it a lot, but the SSD adds some effort also.

Lots of info on SSDs. If Windows installed in BIOS mode you cannot use gpt as suggested for Linux only. Windows only installs to gpt partitioned drives with UEFI not BIOS. One advantage of gpt partitions is all partitions are primary.

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

I always install Ubuntu in about 25GB / partition including /home but am aggressive about moving all data to shared partitions. With the SSD the shared data partitions will be on the rotating drive and just the operating system on the SSD. 

Old MBR partitioning only allows 4 primary partitions and Windows normally uses 2 primaries. One is a small 100MB boot/repair and the other the main install. You can use one primary as an extended which is just a container for logical partitions, but then can create many logicals inside the extended.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by darkod on 2012-07-28
> **homesplat said:**
> How do you decide what portion to dedicate to each OS?  What is the purpose of dedicating a different size to each?  And what is the difference between a swap and a logical partition?

The size you allocate to each OS depends on what you use more, the programs you have installed, etc. You said this is the first computer you built, but that doesn't exclude using a computer now that you didn't build. :) If you are using any computer now, with more or less all programs you plan to use on the new one, check out how big is your C: partition and how much other data you have on other partitions, if any. That will give you an idea how much space windows needs.
If you are also using linux now, do the same, look how much space it takes.

In general linux takes less space, so usually I wouldn't agree to split the ssd 50-50 between them. On the other hand, if you use linux with more programs and large data, it might need much more space than usual.

The swap is a space used when the ram memory gets almost full, to allow the computer to still work fast. In windows it's a swap file usually in C: and in linux it's a separate partition used as swap area. Whether that partition is primary or logical has no difference.
Whether it will be primary or logical will depend on how you organize your disk(s) and how much other partitions you plan to use, also on the partition table used.
With msdos partition table you can have a total of 4 primary partitions, or 3 primary and 1 extended that can contain many logical partitions. That is how you avoid the limitation of having only 4 partitions.
With gpt partition table, there are no primary and logical partitions, all are the same and of course you can have much more than 4.

---

### Post by homesplat on 2012-08-02
Thank you for all of the information.  I will do my research this weekend and see if I can figure out how to do this.  I'll let you know how it went.

---

### Post by adad on 2012-08-04
These instructions worked for me:

[http://brizoma.wordpress.com/2012/08/04/running-ubuntu-and-other-linux-flavors-on-an-ssd/](http://brizoma.wordpress.com/2012/08/04/running-ubuntu-and-other-linux-flavors-on-an-ssd/)

---

