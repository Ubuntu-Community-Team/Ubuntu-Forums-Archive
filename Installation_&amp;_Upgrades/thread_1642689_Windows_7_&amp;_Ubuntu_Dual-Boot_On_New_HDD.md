---
title: "Windows 7 &amp; Ubuntu Dual-Boot On New HDD"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by Dynamata on 2010-12-10
I have a new 1.5TB HDD & want to dual-boot Windows 7 Ultimate (32 Bit) & Ubuntu 10.10, I want 2 partitions for Windows: OS & storage, 3 for Linux: Root, Swap, Home (I guess). Which O.S to install first & what size to make the partitions? :|

PC:__HTPC (1 HDD)
MB:__ASUS P5Q-EM
RAM:_2 GB

---

### Post by oldfred on 2010-12-10
Do not know for sure about windows. I have heard the minimum is 30GB, but with all the space you have you can easily make it larger, but not too large see below. You also do not have to fully partition it initially, but then make sure the extended partition is last, so you can expand it into the empty space.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

The reason I create extra / is so I can have more than one install even if it is just the next Ubuntu. As I like clean installs, it can be handy to have a full working version to look back at for some setting or to boot if new version has issues. I have old install and alpha installed now.

Systems work better is system is separate from data. System files are closer on drive and load slightly quicker, and if you have to reinstall system windows or Ubuntu your data does not have to be reinstalled. You still need good backup and chkdsk on NTFS partitions, just like Ubuntu runs fsck every 30 boots.

I have loaded lots of applications and used about 6GB in /. My /home is only about 1GB of mostly hidden files and folders of user settings with some misc data, but I aggressively move any folder hidden or not that is just data to a data partition.

---

### Post by dmp2010 on 2010-12-10
I currently have Win 7 and Ubuntu in my desktop. I am now installing dual boot in my laptop with 500gig hard drive. This is my plan.

1. Primary 1 - 200 gig - Win 7

2. Extended 
Logical 1 ~ 122 gig  - Ubuntu (First logical drive. You can have multiple logical drives)
     Swap 2 Gig (same size as my laptop RAM)
     /Home 100Gig
     / 20 Gig

3. Primary 2 - 150Gig Storage NTFS (shared between both OS)

4. Primary 3 - 20 Gig - Unallocated for future expansion of other partitions.

Planned steps:
1. I will install Windows 7.  
2. I will install Ubuntu in an Extended partition. 
3. I will create the other partitions as listed. 

Not sure about the steps 2 and 3 but you must install Win 7 first as indicated in step 1 (based on what I read and seems to work in my desktop).  Hope this helps.

---

### Post by Dynamata on 2010-12-10
Sorry, forgot specs :oops::

PC:__HTPC (1 HDD)
MB:__ASUS P5Q-EM
RAM:_2 GB

---

### Post by Dynamata on 2010-12-11
I know Linux can read NTFS now but would not adding a FAT partition be a good idea, just in case? also I don't like the idea of Linux & Windows sharing a "home" partition. Maybe giving each their own storage partition would be safer? :-|

---

### Post by oldfred on 2010-12-12
No you can not share a home partition as in Ubuntu home is a system partition with your user settings. But /home also is the default for all your data. Data can be shared in a NTFS partition. 

I have both a ext3 Linux data partition for data I know I will not need in my XP (most of it now) and I still have some data in a shared NTFS partition. I still have firefox & thunderbird profiles in the NTFS partition as originally I was booting back and forth a lot.

I do not recommend FAT unless you have to have it for compatibility with xbox, cameras, or other devices (usually Flash) and only for small partitions. FAT has a hard limit of files being only 4GB. If you copy a large file to a FAT partition it may not tell you it will be destroyed, as it just writes the first 4GB. It also is not journalized. That is ok for small partitions, but recovery of large partitions is then very difficult.

---

### Post by Dynamata on 2010-12-14
Very interesting, I was not aware of the 4GB FAT limit. After some more research I've decided on this scheme, although I've not determined all the partition sizes:

Windows_____________________Ubuntu
[ 80gb boot ntfs ][ ?gb ntfs logical ][ 500mb /boot ext4 jfs ][ 20gb / ext4 jfs ][ / 2 ][ 2.5gb swap ][ ?gb /home ext4 jfs logical ][ 10gb fat logical ]

I included an extra / for good measure, hope I've got it right. :cool:

---

### Post by Quackers on 2010-12-14
Most systems don't benefit from a separate /boot partition. Some can but most don't.

---

### Post by Dynamata on 2010-12-14
> **Quackers said:**
> Most systems don't benefit from a separate /boot partition. Some can but most don't.
I was following this:

[http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/2/](http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/2/)

I don't usually add a /boot, so I won't.

---

### Post by oldfred on 2010-12-14
+1 on Quackers recommendation.

Overload of info on why no /boot:
Most desktops do not need /boot. If you experiment with btrfs as a file system it does not support booting yet, you then you have to have a /boot. Some very old systems have a 137GB boot limit so a /boot may be required if system in not totally within the first 137GB. Servers with RAID or LVM may work better with a /boot. But in all cases a /boot makes maintenance slightly more difficult.

---

### Post by Dynamata on 2010-12-15
If I got the sums right, this should do it:

Windows_____________________Ubuntu
[80gb boot ntfs][500gb ntfs logical][25gb / ext4 jfs][25gb / 2][2.5gb swap][500gb /home ext4 jfs logical]
[10gb fat logical][357.5~ empty]

:cool:

---

### Post by Dynamata on 2010-12-18
It's done but took 8 hours, I had to scrap my carefully laid plans & use trial & error. wanting partition sizes rounded out to even numbers I used the 1024 rule:

"Here's how to figure the true capacity of your HDD. You have an 80GB drive, so in manufacturer's terms, that means:
   80 x 1,000,000 = 80,000,000 bytes
   But if you divide that number by 1,048,576 you'll get the true capacity...
   80,000,000 / 1,048,576 = 76.29 GB"
  [http://www.computing.net/answers/hardware/hdd-lower-gb-size-than-actual-size/41025.html](http://www.computing.net/answers/hardware/hdd-lower-gb-size-than-actual-size/41025.html)

(Ironically Windows Explorer changed 500GB to 499GB etc)

Unlike Windows XP, Windows 7 Installer wouldn't let me go back  & adjust partition sizes & took a stupid amount of time between operations, it wouldn't let me boot off the CD  claiming missing MBR. After a few attempts I gave up & used GParted on the Ubuntu CD to clear the HDD & install Windows.

I couldn't figure out how to fit all the partitions in while satisfying the 4 primary partitions rule:

1. Windows System Reserved
2. Windows 7
3. Ubuntu /
4. Extended

How do you create extra /? After installing Windows I used GParted to create the required partitions, left an empty partition for Ubuntu OS then used the Ubuntu installer to create / & it worked! Anyway here's the result:

[IMG]http://www.dynamata.com/images/install%202.jpg[/IMG]

When I boot into Windows the file explorer doesn't see Ubuntu so the Windows partitions appear next to each other:

[IMG]http://www.dynamata.com/images/windows.jpg[/IMG]

Thanks for the help, got there eventually. :cool:

---

### Post by Quackers on 2010-12-18
Nice one :-)
Go and have a sleep now :-)

---

### Post by Dynamata on 2010-12-18
I just noticed that maybe I could've put the swap outside the extended partition & why do the 1st 3 partitions go 1 2 4?.

---

### Post by Quackers on 2010-12-18
I don't think you want any more partitions outside the extended. You've now got 4 primary partitions! No more for that disc. Any further partitions must be inside the extended partition. (You can extend the extended partition to the end of the disc first though ).

---

