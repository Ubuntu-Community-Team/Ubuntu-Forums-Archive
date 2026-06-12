---
title: "Installing ubuntu killed my Windows XP partition"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by Jmizzle on 2010-05-24
Ok, so I was trying to do dual boot Windows XP and Ubuntu 10.04, but in the process, something went pretty wrong.

My first problem was repartitioning Windows XP, once I figured out I needed to defragment, and run chkdsk /f, everything seemed like it was going fine. I booted up gparted off a usb, and resized the partition from 112gb to 90gb. (I had like 30gb+ or unallocated space, so there was no issue there)

It seemed to repartition fine, there was no error, but when I restarted my system, I was greeted with a BSOD. It had an error that said 'inaccessible boot' or cant boot into OS, or something, I don't really remember anymore.

I figured I should be able to fix that problem easy enough, so I thought I would install Linux fist. I booted up Ubuntu off another usb drive and tried to install it along side of windows. I don't know if I installed it correctly though. I can still access my files, but they all look like this.
[IMG]http://img689.imageshack.us/img689/4544/37972504.png[/IMG]
So I don't know what to do.

Also, after I installed Ubuntu, when I start my computer, it boots straight into Ubuntu. There is no grub boot manager, or windows boot manager.

And another thing, my Windows file system is FAT16 now, and I'm sure it was NTSF before.. I have no idea how to fix this. I'd really just like to be able to gain access to my files.

---

### Post by Herman on 2010-05-24
Wow!

You should probably not do anything until after you make a backup of the entire partition as it is now, using a dd command and some other disk such as a USB external hard drive.

After that you can try some ideas to recover your date.

You can post some diagnostic information anytime, such as the output from 'sudo fdisk -lu', so somebody can check your partition table and maybe see if there's anything wrong with it.

---

### Post by Jmizzle on 2010-05-25
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdb34db34

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   189422414    94711176   3c  PartitionMagic recovery
/dev/sda2       189422415   198691919     4634752+  82  Linux swap / Solaris
/dev/sda3       198691920   199273671      290876   83  Linux
/dev/sda4       199274494   234440703    17583105    5  Extended
/dev/sda5       199274496   232880127    16802816   83  Linux
/dev/sda6       232882176   234440703      779264   82  Linux swap / Solaris


There is the output from 'sudo fdisk -lu'

So, I don't have an external hard drive to backup into, I might try online storage?

Is there anything I can do to get this thing going?

---

### Post by Herman on 2010-05-25
Okay, according to fdisk, your Windows XP partition, which used to be formatted with NTFS is obviously now flagged as a 3c PartitionMagic recovery partition.
It seems odd that GParted would flag the partition table with a file system type that belongs to a proprietary partition editor like Partition Magic, I didn't know GParted could do that. 
According to the [List of partition identifiers for PCs]("http://www.win.tue.nl/%7Eaeb/partitions/partition_types-1.html"), 
> **3c  PartitionMagic recovery partition**Cody Batt (codyb@powerquest.com)  writes: When a  [PowerQuest]("http://www.powerquest.com/") product like [PartitionMagic]("http://www.powerquest.com/en/partitionmagic/index.html")  or [Drive Image]("http://www.powerquest.com/en/driveimage/index.html")  makes changes to the disk, it first changes the type flag to 0x3C so that the OS won't try to modify it etc.  At the end of the process, it gets changed back to what it was at first.  So, the only time you should see a 0x3C type flag is if the process was interrupted somehow (power outage, user reboot  etc). If you change it back manually with a partition table editor or  something then most of the time everything is okay.It could be that you only need to fix the partition type flag in the MBR or it turn out that the partition type flag in the MBR is a symptom of another problem.
If there are problems in file system they can usually be fixed by running CHKDSK /R if you can get Windows to recognize the drive.
TestDisk is the program I use for repairing or re writing a MBR, and that program should be in your GParted USB if you're using the same GParted as I use.

I don't know how much your data is worth to you, but it's not a good idea to do anything until you have another copy of it just in case working on it might cause further complications.
You really should look for some other disk you can clone the entire partition to with a dd command.
Remember, as long as you don't touch it, your data will wait virtually forever if needs be, until someday when you happen to have the right resources available.

---

### Post by perspectoff on 2010-05-25
> **Herman said:**
> Okay, according to fdisk, your Windows XP partition, which used to be formatted with NTFS is obviously now flagged as a 3c PartitionMagic recovery partition.
It seems odd that GParted would flag the partition table with a file system type that belongs to a proprietary partition editor like Partition Magic, I didn't know GParted could do that. 


Yeah, I've never seen GParted use PartitionMagic partition flags.

---

### Post by Jmizzle on 2010-05-25
I forgot to mention that I was messing around with PartitionMagic a lot before I decided to use gparted.

---

### Post by Herman on 2010-05-26
> I forgot to mention that I was messing around with PartitionMagic a lot  before I decided to use gparted.:) That's okay, we'll still try to help you as much as we can, I don't know much about Partition Magic though.

I think that Partition Magic has marked your partition table  like that for a reason. The reason is, it knows that something went  wrong during a partitioning operation and so it has left a signal there  that should tell the user to look for expert help, (probably implying  help from the company that now owns Partition Magic, which is Symantec I  think.) You should probably get in touch with Symantec first and see if  they will help you for free or not. If they will, or even if they will only charge a moderate fee, you can probably  relax and follow whatever instructions you get from their tech support. 

Please come back here and let us know how you get along.
If they won't help you, or if they will charge you a lot of money for their services, then we may be able to use free software to fix your problems but there's no guarantees.
It might be simple and quick or it could turn int quite a lengthy process, we never can tell with computer problems. :)

---

### Post by Jmizzle on 2010-06-05
Okay, I got an external hard drive, and that data is all backed up. I'd like to start trying some things to get my data back :).

---

### Post by Herman on 2010-06-06
It's best if you can use a dd command to make an exact copy of the  entire partition. If you only copied and pasted the corrupted files they may not do you any good.

I would start by using TestDisk to fix the partition table and get rid of that  0x3C type Partition Magic flag, if you have tried and can't get any help from the vendors of that program. Did you ask them for help?

TestDisk is a program that can  be installed in Ubuntu or in the Ubuntu Live CD (temporarily), which can scan your hard disk for file systems and you can use it to write you a new partition table with the partitions you select. It will be interesting to find out if TestDisk will recognize the remains of the corrupted file system as NTFS. I'm hoping it will. If that works then you can at least fix your partition table. 
The partition table isn't your problem though. Your main problem is either in the file system, in which case a file system check just might fix it for you, or the files themselves, in which case I don't know. I would try CHKDSK /R to see if fixing the file system does any good. 

Failing that, you can try data carving with photorec, a program that comes with TestDisk, and that ignores both the partition table and the file system, and instead tries to read the files off your hard disk and you can use it to copy them, (or what's left of them), to some other disk or partition. Sometimes you can recover a lot of files intact with photorec, but other times you'll only get fragments of files. Even if you only get file fragments, if it's important data you might still be able to get some of it back, but it will be a lot of work sorting through it all. The fact that you defragged would help your chances of getting more of your files back intact.
You may even find some of your files in areas of your Ubuntu partition as there will probably be large areas of that which have not yet been overwritten, so it's worth also scanning your Ubuntu partition with photorec.

Here are some links for you, 

[**Ubuntu Rescue Remix**]("http://ubuntu-rescue-remix.org/")  
Ubuntu Rescue Remix is a GNU/Linux live system which runs from CD or USB flash device. It provides the data recovery specialist with a command-line interface environment equipped with the best free-libre, open source data recovery and forensics tools available.
There is also a special [Ubuntu Rescue Remix Web  Forum]("http://ubuntu-rescue-remix.org/forum") where you may ask for expert help with your problems. 

[**DataRecovery**]("https://help.ubuntu.com/community/DataRecovery") - Ubuntu Community  Docs 
Please read the Ubuntu Documentation page on data recovery before you do anything. 

[COLOR=#c0c0c0][TestDisk - CG Security]("http://www.cgsecurity.org/wiki/TestDisk") the official homepage for TestDisk,  TestDisk has its own excellent  illustrated documentation.

[PhotoRec - CG Security]("http://www.cgsecurity.org/wiki/PhotoRec")  the official homepage for PhotoRec, TestDisk's companion application,  so you can read the official documentation. 

[/COLOR][COLOR=#c0c0c0][]("http://www.geocities.com/thestarman3/asm/mbr/DataRecovery.htm")[/COLOR][COLOR=#c0c0c0][How to recover lost files  after you accidentally wipe your hard drive]("http://www.linux.com/articles/56588") by Shawn Hermans  -  Recommended if you're going to use PhotoRec

[Recovering  Windows files with a Ubuntu CD III: deleted files]("http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/") - Ubuntucat [/COLOR][COLOR=#c0c0c0]by aysiu - [/COLOR][COLOR=#c0c0c0] also recommended if you need to use  PhotoRec 

[/COLOR][COLOR=#c0c0c0][Disk Recovery]("http://ubuntuforums.org/showthread.php?t=447849"),  a Ubuntu Web Forums thread, particularly [/COLOR]see                                                                                     [brennydoogles]("http://ubuntuforums.org/member.php?u=258498")'  prorganize.sh script  -  for use with PhotoRec

---

