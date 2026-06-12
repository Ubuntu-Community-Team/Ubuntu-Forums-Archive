---
title: "Need Help on Partitioning &amp; Installing Ubuntu - Linux Noob"
date: 2006-02-19
forum: Installation &amp; Upgrades
---

### Post by animaster on 2006-02-19
Hi all, Ubuntu-ers!

I'm thinking of installing a Linux distribution on my current system, and then I'm crossed by here somehow. I'm surprised by the way community of Ubuntu supporting the distro.:o 

And now I'm going to install Ubuntu on my PC. I'm a Linux noob (yep, totally newbie ! :p ), so before installing, I've done some research on the forum about guide for installing Ubuntu safely.

I've read Herman's guides of dual-booting Ubuntu and Windows which are really nice (the illustration sure helps a lot:D ). But I'm not sure whether it covers my "requirements" or not.

Here's my HDD's partitions: (I only have 1 HDD with a total of 120 GB)

_Windows_
Primary - 20 GB - NTFS - Windows (C) - Windows XP SP 2
Extended - 15 GB - NTFS - Programs (D)
Extended - 15 GB - NTFS - Games (E)
Extended - 60 GB - NTFS - Multiuse (F)
-------------
_Linux_
Extended - 10 GB - Unformatted - *This is where I'm going to install Ubuntu*

note: This extended partition was unformatted because I don't know what Ubuntu's optimal filesystem is. :confused: 

Does Ubuntu have to be installed on primary partition ?
Are there any good guides on how I should install the Ubuntu with above specs ? Hopefully the guide will come with some illustrations. :p 

Thank you very much for your help. I really appreciate it. :-D

---

### Post by el3ktro on 2006-02-20
Hello,

well other than Windows Linux can be installed anywhere on your harddisk. 10GB is just fine for a test-drive install. The best is you just pop the Ubuntu CD in and tell the setup program to use the free space of your harddisk for Ubuntu. It will create one large partition for the system itself with an Ext3 filesystem, which is a good choice & definitely superior to NTFS :-) The second partition will be a small swap partition, similar to Winowds' swap file. When you consider keeping Linux & dual booting it would be a good idea to have a FAT partition to share files between Linux & Windows, since Linux can't write on NTFS partition due to licensing issues. So if you want this and if you can do it somehow, I'd convert any of the two 15GB or the 60GB partitions to FAT so you can share your multimedia stuff etc.

Tom

---

### Post by animaster on 2006-02-20
Thank you very much ! I'm going to try it now.

Err ... one more question:
You said that Linux can't write on NTFS partitions, but it can read from the partition, right ?

---

### Post by el3ktro on 2006-02-20
[QUOTE=animaster]Thank you very much ! I'm going to try it now.

Err ... one more question:
You said that Linux can't write on NTFS partitions, but it can read from the partition, right ?[/QUOTE]

Well okay Linux itself has a read-only NTFS driver, so yes it can read from NTFS perfectly. There exists a program called "captive" which uses the original NTFS driver from Windows (2k/XP) to read AND write to NTFS, but you need a copy of Windows for this, and write access is pretty slow. I don't know how slow though, but at least it works :-)

Tom

---

### Post by ourmanritter on 2008-04-15
Hi, another noob to linux...

i belive my question's answered, but just so i'm clear...

i have a desktop system that i'm almost finished building for my wife, which as of now i'm planing to install  windows xp pro on (she requested it, wants to use outlook for calendar etc., can't find satisfactory linux drivers for her sound card). however, i anticipate that i'll be installing ubuntu on this system in the future (after i've convinced her), as i'll be doing on some other older systems i will be refurbishing. 
 
my assumption then is that i should format the partitions that will be containing data files such as documents, photos, audio/video files, etc., with FAT32 so that a future install of ubuntu will easily be able to read/write to this/these partitions, as ntfs would not be interoperable.  

thank you in advance

---

### Post by luvr on 2008-04-15
> **ourmanritter said:**
> my assumption then is that i should format the partitions that will be containing data files such as documents, photos, audio/video files, etc., with FAT32 so that a future install of ubuntu will easily be able to read/write to this/these partitions, as ntfs would not be interoperable.
That **used** to be the case, but the new Ubuntu release, 8.04, should have full read/write support for NTFS built in.
Even under 7.04, you can safely read and write NTFS filesystems, with a separate package that you need to install from the Ubuntu repositories.
In fact, there's no longer any need for FAT32 partitions.

---

### Post by ourmanritter on 2008-04-15
> **luvr said:**
> That **used** to be the case, but the new Ubuntu release, 8.04, should have full read/write support for NTFS built in.
Even under 7.04, you can safely read and write NTFS filesystems, with a separate package that you need to install from the Ubuntu repositories.
In fact, there's no longer any need for FAT32 partitions.


wow, ok...

however, is it truly advantageous to use NTFS anyway? i'm researching this, but it'd be interesting to hear some of your opinions. 
sorry for not looking this up, but what system does ubuntu use then? or will that be changing with the latest version? i assumed it was FAT.

thanks luvr,
 i mean thanks, screen name l, u, v, r, :(  j/k

---

### Post by luvr on 2008-04-15
> **ourmanritter said:**
> is it truly advantageous to use NTFS anyway?
Well, NTFS will use smaller allocation units than FAT32, particularly on big partitions. In other words, it will result in less *"wasted space"* on disk.

> what system does ubuntu use then?
It uses a Linux file system--typically **ext3**--which is not accessible (without additional software) from Windows.

---

### Post by ourmanritter on 2008-04-15
ah, yes... thanks again.

---

