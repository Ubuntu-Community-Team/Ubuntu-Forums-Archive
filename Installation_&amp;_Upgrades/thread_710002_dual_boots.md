---
title: "dual boots"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by jwxie on 2008-02-28
hey guys, if you guys don't mind i just want to get something clear here

if i want to do dual boot
first i reinstall my xp, 
let say 80GB

and after the XP, I am going to install my 7.1 Ub and ready to parition
i want to try manaual, here are a several cases

1. ram 128mb , if so, how many mb / gb do i need for swap? In general, how much space is 7.1 going to take beside the swap...

2. ram 1GB, if so, how mnay mb / gb do i need for swap?


and lastly, how do i set the dual boots, when and how if you can tell me that's great, than,k you

---

### Post by uberlube on 2008-02-28
You should always use manual setup for the partitions. And your SWAP should always be 2wice your ram so 1 gig of RAM = 2 gigs SWAP. and yes install Windows first on its own NTFS partition, it makes it easier for the GRUB to detect it when it is installed. If you would like a great tool for partitioning and computer maintenance use Parted Magic:

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

---

### Post by TrendRat on 2008-02-28
jwxie
Here are a few links on dual boots:
[http://ubuntuforums.org/showthread.php?t=56723]("http://ubuntuforums.org/showthread.php?t=56723")
[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/")
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html]("http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html")

It's a good idea to read a bit before tackling this, it can go smooth as silk or it can be tricky.  Sounds like your are starting with a clean drive, which is good.  If you have data on the drive please back it up.

You can also try [Wubi]("http://wubi-installer.org/"), I used it after some struggle with the other methods and it worked great for me.

I'm not an expert on swap files, but I think about twice the RAM is normal, and 2GB is the max

Good Luck
TrendRat

---

### Post by uberlube on 2008-02-28
Hello to a fellow Albertan :)

---

### Post by TrendRat on 2008-02-28
Hello uberlube, always good to find another Albertan in the crowd... :)

---

### Post by uberlube on 2008-02-28
I havent met to many people in here from Edmonton, but there seems to be quite a few from Calgary.

---

### Post by zvacet on 2008-02-28
1.root =10GB                            mountpoint /
2.home=rest of free space       mountpont /home
3.swap=256MB

[Here](http://www.psychocats.net/ubuntu/installing) is good giude if you need something.It is good to read it before you start.

---

### Post by mi_were on 2008-02-28
Instead of a dual boot consider going with vmware since it seems like you system has the resources.

---

### Post by zvacet on 2008-02-29
@ **jwxie**

I overlooked your ram.It will be better to install Xubuntu with alternate CD from 
[here.](http://se.archive.ubuntu.com/mirror/cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

---

### Post by jwxie on 2008-03-01
i think i will install dual boot on my 1GB P4 desktop for personal use, while the 128MB laptop, i had already installed the 7.1. When I replied this, I am now using the 7.1, yeah, yummy.

let me try to do dual boot now^^

---

### Post by jwxie on 2008-03-01
i have a question about the partition

> a Ubuntu partition, a Windows partition, and a FAT32 partition in the middle to share data between the two operating systems. This is frequently recommended on the Ubuntu Forums as a good way to partition a drive, since both Windows and Ubuntu can natively read from and write to FAT32.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

If i have a 117GB HD
and I need my XP to be install with Adobe CS3 Premium and other large installtions, which may takes up at least 20 GB, 

i want to know if i set like the followings:

NTFS (win): 25 GB
Linux Swap: 2GB
Liux /root (included home): 30GB  <~~~ do i really need that much for 7.1????
Shared Data FAT32:  the remaining partitions

Q1:   Then, my question is, how do i use the Shared spaces for both OS? Let say I finished 95% of my NTFS, and I need to download a movie via XP, and the video will be 3 GB, how do i set to save the files onto the Shared space?

Q2:   I remembered that FAT32 had a limitation to file that is larger than a certain GB (i think it's either 3GB / 4GB), right?  Just like that, if I am going to use FAT32 for shared data, when I am at XP, will the process of getting these data becoming slower than from NTFS does????

Sorry folks, thank you

---

### Post by jwxie on 2008-03-02
ok folks, seems my post is dropped to 100meter down
i did my job last night, and today i was able to fix my "WHITE SCREEN" problem

i entered "Computer FIle Browser"
and I want to check how many dirves do I have

I have 22.GB sda1 <~~~~ this is NTFS windows, only for application

42.9GB sdb1, it stores my musics, and photos

Filesystem, everyone knows this is the ubuntu ext3, and I have my root and my home in the same place, yes.... i am still beginning, don't want to try separate home directory

but what I am missing is the FAT32 system.

I thought I should get that partition shown, so i can save files on both system.....

how do i correct this????

thank you

---

### Post by jwxie on 2008-03-02
anyone please??

---

