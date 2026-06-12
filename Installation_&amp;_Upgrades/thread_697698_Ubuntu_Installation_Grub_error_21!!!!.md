---
title: "Ubuntu Installation Grub error 21!!!!"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by Ubun2_h8r on 2008-02-15
Okay its been nearly a whole day now i've been trying to sort out Ubuntu so that it can work properly with no avail. After installing Ubuntu on my internal hard drive with no problems, i restarted to find an error message appear saying something along the lines of grub 1.5, error 21. I've spent all day and night looking through different forums and searching for my problems and have tried many things, all of them have failed. Now im just about ready to give up, I registered here purely because i want a way to either get Ubuntu working properly or start Windows again from scratch. Luckily, before attempting to install Ubuntu i backed up all of my personal files onto numerous external hard drives, so if it means i need to restart Windows from scratch, i am more than willing, however i don't have the Windows xp recovery Cd or a floppy disk drive.

The specs for my PC are as follows

Sony VGC RC-204 Media Edition
2x300GB SATA Hard Drives
6GB RAM
Intel Pentium D Processor.

now at this moment in time im stuck on the live cd of ubuntu and ive deleted the partitions it created (after trying to install it twice) the second time i changed the grub thing from (hd0) to (hd1)

i must stress im new to this software and i am not very familiar with command prompts etc i have guessed my way to where i am now, but after going through many forums ive started understanding the problem, 

Can someone please take the time and patience to help thanks in advance.

---

### Post by logos34 on 2008-02-15
menu.lst may be getting the **root** wrong.  Try the suggestions [here.]("http://users.bigpond.net.au/hermanzone/p15.htm#21")

You might want to post your partitions.  Open a terminal on the live cd and type 

**sudo fdisk -l**

post it.

---

### Post by Herman on 2008-02-15
[     Grub error 21]("http://users.bigpond.net.au/hermanzone/p15.htm#21").? 

That means the hard disk you're trying to boot doesn't exist! 

You should get your self a copy of [Super Grub Disk]("http://sgd.benjamin-butschko.de/") and after the installation is finished, try to boot it the normal way first. If it still doesn't boot, you should be able to boot it with Super Grub Disk if it's bootable at all.

Besides being useful to boot with, Super Grub Disk will certainly give you access to [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") which is useful for testing and experimenting to try to determine what the problem could be so we can probably fix it.

Does or did this computer have any kind of RAID at any time?
Have you checked your BIOS settings to make sure both of your hard disks are properly set up and detected in your BIOS?

Regards, Herman :)

---

### Post by Ubun2_h8r on 2008-02-15
opened a terminal and typed sudo fdisk -l got this:



Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc1b82823

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         912     7325608+  12  Compaq diagnostics
/dev/sda2   *         913       31307   244147837+   7  HPFS/NTFS
/dev/sda3           31308       72961   334585755    f  W95 Ext'd (LBA)

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0fd93b00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2           34546       36481    15550920    5  Extended
/dev/sdb5           35259       36481     9823716   82  Linux swap / Solaris
/dev/sdb6           34546       35258     5727109+  82  Linux swap / Solaris

Partition table entries are not in disk order


no idea about the raid thing, but i checked the bios and both hard drives are detected

---

### Post by Herman on 2008-02-15
>  Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite) I'm not sure what that means exactly, but there's a good chance that's your problem.

---

### Post by Herman on 2008-02-15
:)
Boot your Ubuntu Live CD and open a terminal.
Do 'sudo fdisk /dev/sda'
```
sudo fdisk /dev/sda
```It should repeat the same Warning message.

You can type 'm' after the prompt for a list of commands and what they are for.

Press 'w' to re**w**rite the partition table. (correctly we hope).

Reference Link: [http://ubuntuforums.org/showthread.php?t=437814](http://ubuntuforums.org/showthread.php?t=437814) thanks to Najand.

EDIT: I tested this procedure in one of my computers and it rebooted without any problems to is seems as if that command is safe enough. If anything did go wrong I think i would use TestDisk next.

---

### Post by Ubun2_h8r on 2008-02-15
okay this is what happened:


ubuntu@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 36481.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
ubuntu@ubuntu:~$ 

then it just stopped???

---

### Post by Herman on 2008-02-15
Yes, just type 'exit' to close the terminal and your problem should be fixed. :)

EDIT: Or type 'sudo fdisk -lu' again to make sure first, before closing the terminal.

---

### Post by Discov3ry on 2008-02-15
Are you setting it up as a RAID 1 setup?

Can you post /boot/grub/menu.lst?

---

### Post by Herman on 2008-02-15
:) Hello Discov3ry
Have you seen this video: [Installing Ubuntu Part2]("http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2") , Ubuntu Screencasts?
It might contain something interesting for you, I don't know much about RAID.

Regards, Herman :)

---

### Post by Discov3ry on 2008-02-15
Hello Herman :)

Thanks for the video, I don't know RAID 1 and I don't know Linux. It should be a good lesson for me :D

Ubun2_h8r
Did you get it fixed?

---

### Post by pcjunkie on 2008-02-16
With SATA drives "mixed" with IDE drives I found that if you go into the BIOS and under boot device or similar (where you set the boot order, i.e dvd, HDD, Floppy etc) there is a menu item for setting exactly which disk **is** the boot disk. 

If in there you can see a list of drives connected. 

1 SATA 1 Seagate xxxx 1600 eg
2 SATA 2 Seagate xxxx 2800 eg
3 IDE Master Maxtor xxxx.xxx.xxx 450g eg
4 IDE slave WD cameo blah blah xx.xxxx.xxxxx 500g

It should not display DVD's or anything else but what is on the IDE SATA bus physically

The Order can be changed using arrow keys and + - Keys but only the disk highlighted will change order, This is not the standard boot order / priority but a sub menu under manage disks or similar wording...

You can be sure that SATA1 is where the (HD0,0) boot is by default, If windows is present on this mixed bag of goodies you may loose boot if Ubuntu fails to detect it.

If it does fail you can use this list (F 8 or F 10) at start up to change the boot drive (one time only then it resets) to find where stuff went, If it failed to boot from any drive I will be surprised,To make a proof positive boot I partitioned the first part of SATA1 and made it (HD0,0) (FAT32 (optional but both OS's can see read it)) in my map and installed grub manually into it. It found the WINNT boot on disk SATA2 and everything is fine. 

Check you Bios first, then try installing Grub, if fail try F8 at startup to set the disk to boot from (one time only) and see where your PC is pointing the HD0 to. Once you find the disk go back and see where you BIOS is pointing. It should be the same.

---

