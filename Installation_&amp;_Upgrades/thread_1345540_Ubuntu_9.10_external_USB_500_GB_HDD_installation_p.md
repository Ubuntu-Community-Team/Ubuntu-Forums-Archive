---
title: "Ubuntu 9.10 external USB 500 GB HDD installation problem"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by macalaki on 2009-12-04
Hi ... I decided to create this thread after two days of trying install Ubuntu on my external Samusng S2 500GB HDD. I've searched the web and this forum also, but I was not able to find the complex solution. So here is my issue (maybe no issue for Linux Gurus):

- I'am not expert, but familiar with HDD partitions and filesystems and related stuff
- So before installation of Ubuntu from bootable USB stick I've created the ext3 Linux partition on my external USB HDD using Linux fdisk. The first I've noticed was warning that disk logical sector size is 1024 instead 512. But partition was successfully created and written to partition table. I've just created one primary partition to plan add extended one with linux swap and some FAT32 shared area latter during installation process.
- Then I've run the installation and during manual disk partitioning the gparted showed dialog window that 1024 logical sector size is not the best for it. Another think I've noticed that it's showed wrong size of disk (half size actually). But I click continue. I was surprised that gparted shows disk as unallocated and it crashed if I try to create partition table.
- I've tried to use also partitioning utility in Win to partition my disk, but the result was always the same. Anyway the ubuntu installation can recognize disk and partitions without problem. My problem is only installation.

Thanks for reading this post :), and I will appreciate any help which ease my life with ubuntu...   

Regards, Ivan...

---

### Post by darkod on 2009-12-04
You should not create partitions in advance for ubuntu. You can do all of that during the install. Otherwise you still have to re-mount existing partition which is double the job. Plus 9.10 comes with the newer ext4 as opposed to ext3.
So if you boot with the ubuntu cd and select Try Ubuntu option and open Gparted, how does it show your 500GB hdd right now? Correctly? Half sized?

---

### Post by macalaki on 2009-12-04
Thanks for the quick response. I've done suggested actions and Gparted showed only half size of the real HDD size. Any further suggestions, what I should try ? Is it any difference between booting from USB stick and CD ?

---

### Post by macalaki on 2009-12-08
Nobody can give some light to this issue ?

---

### Post by darkod on 2009-12-08
> **macalaki said:**
> Thanks for the quick response. I've done suggested actions and Gparted showed only half size of the real HDD size. Any further suggestions, what I should try ? Is it any difference between booting from USB stick and CD ?

That might be because of the change from 512 to 1024 you did with fdisk I guess. I never tried something like that myself so I can't be sure.

If you have important data on the ext hdd move it somewhere, and I suggest using Gparted to delete all partitions, then create ntfs partition if you need one there, and leave the rest of space unallocated for ubuntu. I hope that would make the drive to be recognized with full size. Do not create partitions for ubuntu in advance, no need. It even complicates things further.
Then when you start the install process you will create the needed partitions manually or with guided install, depending what you want.

And next time use Gparted from the LiveCD rather then using fdisk. It's very powerful and can easily be made a mistake in text mode.

---

### Post by macalaki on 2009-12-08
Hi Darko, thank you. I will try to repartitioning disk according your suggestion. The 1024 logical sector size was there from factory settings, but I was not able to change it using fdisk to 512. This is maybe the basic problem of this disk.

---

### Post by Bartender on 2009-12-08
> **darkod said:**
> And next time use Gparted from the LiveCD rather then using fdisk. 

+1  I've done a fair amount of partitioning projects (primary, extended, logicals, NTFS, ext3, ext4, etc.) without ever having to resort to the command-line fdisk.  I've used gparted on the Ubuntu Live CD, but prefer to use GParted LiveCD.

---

### Post by macalaki on 2009-12-08
I'am trying to do this for first time, but no success yet. :) See (I've created the bug report for parted utility):

I'd like to partition my USB 500GB Samsung S2 disk. It shows that logical sector size is 1024. As there is recommendation in FAQ to use gpt type partition table I invoked following command: (parted 1.90 shifted with gparted live 0.4.8-6)

mklabel gpt
in interactive parted mode. Command failed with following error:

Assertation (dev != null) at ../../libparted/device.c:365 in function
ped_device_write() failed.
Details:

Model: Samsung S2 Portable (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 1024B/512B
Partition Table: msdos

Model: Samsung S2 Portable (scsi)
Disk /dev/sda: 4883865845
Sector size (logical/physical): 1024B/512B
Partition Table: msdos

Because of this problem I'am not able to install Ubuntu on my portable USB hdd.

Have you seen similar error ?

---

### Post by presence1960 on 2009-12-08
> **darkod said:**
> You should not create partitions in advance for ubuntu. You can do all of that during the install. Otherwise you still have to re-mount existing partition which is double the job. Plus 9.10 comes with the newer ext4 as opposed to ext3.
So if you boot with the ubuntu cd and select Try Ubuntu option and open Gparted, how does it show your 500GB hdd right now? Correctly? Half sized?

Darko I have to disagree with you on this one, but with a condition. I would say newbies to partitioning and OS installations should not attempt to create partitions prior to installing Linux.

It is perfectly safe and logical to create partitions prior to installing Linux- if you know what you are doing. If it was not meant to be one of the ways to install Linux there would be no manual option on the installer.

That being said for a relative newbie or novice I would concur that doing the side by side or use entire disk option is the best way to get Linux installed. But I disagree with the absolute qualification that one **should not create partitions in advance for Ubuntu**. That just is not true.

---

### Post by presence1960 on 2009-12-08
> **macalaki said:**
> I'am trying to do this for first time, but no success yet. :) See (I've created the bug report for parted utility):

I'd like to partition my USB 500GB Samsung S2 disk. It shows that logical sector size is 1024. As there is recommendation in FAQ to use gpt type partition table I invoked following command: (parted 1.90 shifted with gparted live 0.4.8-6)

mklabel gpt
in interactive parted mode. Command failed with following error:

Assertation (dev != null) at ../../libparted/device.c:365 in function
ped_device_write() failed.
Details:

Model: Samsung S2 Portable (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 1024B/512B
Partition Table: msdos

Model: Samsung S2 Portable (scsi)
Disk /dev/sda: 4883865845
Sector size (logical/physical): 1024B/512B
Partition Table: msdos

Because of this problem I'am not able to install Ubuntu on my portable USB hdd.

Have you seen similar error ?

Boot the gparted Live CD and then delete all the partitions in 500 GB disk, click apply. Then make an msdos partition table. Then do what darko said: create an NTFS partition for storage and leave the rest of the space unallocated. Click Apply. Once your disk is set up install Ubuntu to 500 GB disk. Choose the use largest continuous free space option. When you get to the Ready to install window (see below pic) click advanced and choose where to install GRUB. You want GRUB on MBR of 500 GB disk. This way when that 500 GB is not plugged in you boot right to windows. if it is pluggen in you boot to GRUB and choose Ubuntu.

I just noticed something:

Model: Samsung S2 Portable (scsi)
[COLOR="Red"]Disk /dev/sda: 500GB[/COLOR]
Sector size (logical/physical): 1024B/512B
Partition Table: msdos

How is your external disk sda? That is puzzling to me. Why don't you boot into the Ubuntu Live CD with external plugged in. choose "try ubuntu without any changes", when the desktop loads open a terminal and run ```
sudo fdisk -l
``` that is a lowercase L in -l

Paste the entire output back here.

---

### Post by darkod on 2009-12-08
> **presence1960 said:**
>  I would say newbies to partitioning and OS installations should not attempt to create partitions prior to installing Linux.


That's what I meant actually. Trying to keep it short does not sound right all the time. :) The point was that I've seen other threads that most people new to linux/dual boot expect sometimes the partition to be used by default. The mounting concept makes it much different to windows. Linux/Ubuntu will not use it by default because first of all it doesn't have a clue what you plan to do with that partition at all. :)

---

### Post by macalaki on 2009-12-08
Hi, so I invoked the process of partitioning external USB disk again, but nothing helps. Here, are the steps I've done.
1.) The Disk was unallocated and clean before I boot from gparted live CD (latest version 0.5.0-3)
2.) The gparted simply crashed during loading disks, so I've decided to boot from ubuntu live CD and start gparted and other stuff from ubunu environment to get some symptoms.
3.) Attached Disk-Utility.png shows the external USB disk as /dev/sdc with no space allocated
4.) Atatched fdisk-parted.txt contains command which were run from console. The first one shows fdisk -l output before any action was performed:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47ffd57a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6528    52436128+   7  HPFS/NTFS
/dev/sda2            6529       38913   260132512+   7  HPFS/NTFS

Disk /dev/sdb: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         983     7895916    b  W95 FAT32
Note: sector size is 1024 (not 512)

[COLOR="Red"]Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 30400 cylinders
Units = cylinders of 16065 * 1024 = 16450560 bytes
Disk identifier: 0x0003dd81

   Device Boot      Start         End      Blocks   Id [/COLOR] System
```
5.) Snapshot gparted-1.png shows, how the gparted recognises /dev/sdc device. As half-sized actually.
6.) Then I try to create ntfs partition (cca 100GB) using gparted as is shown on gparted-2.png. The gparted has crashed.
7.) What fdisk-l listed after this crash is here (only /dev/sdc)
```
Note: sector size is 1024 (not 512)

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 30400 cylinders
Units = cylinders of 16065 * 1024 = 16450560 bytes
Disk identifier: 0x0003dd81

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]/dev/sdc1               1        6374   102398278   83  Linux[/COLOR]
```
This is strange for me ...
8.) Then I've decided to go from commandline. See points 3.)- 5.) in attached fdisk-parted.txt.
9.) So my conclusion is that parted utility is not able to handle disks with logical sector size != 512, or there is something wrong with Samsung S2, but I'am not sure where the problem could be.
10.)Please check the point 5.) from attached file. After parted crashed, the partition was created only for first half of the disk and then parted crashed.

---

### Post by presence1960 on 2009-12-08
> **darkod said:**
> That's what I meant actually. Trying to keep it short does not sound right all the time. :) The point was that I've seen other threads that most people new to linux/dual boot expect sometimes the partition to be used by default. The mounting concept makes it much different to windows. Linux/Ubuntu will not use it by default because first of all it doesn't have a clue what you plan to do with that partition at all. :)

Understood, sometimes written word is tricky. So we are now in agreement!

---

### Post by presence1960 on 2009-12-08
> **macalaki said:**
> Hi, so I invoked the process of partitioning external USB disk again, but nothing helps. Here, are the steps I've done.
1.) The Disk was unallocated and clean before I boot from gparted live CD (latest version 0.5.0-3)
2.) The gparted simply crashed during loading disks, so I've decided to boot from ubuntu live CD and start gparted and other stuff from ubunu environment to get some symptoms.
3.) Attached Disk-Utility.png shows the external USB disk as /dev/sdc with no space allocated
4.) Atatched fdisk-parted.txt contains command which were run from console. The first one shows fdisk -l output before any action was performed:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47ffd57a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6528    52436128+   7  HPFS/NTFS
/dev/sda2            6529       38913   260132512+   7  HPFS/NTFS

Disk /dev/sdb: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         983     7895916    b  W95 FAT32
Note: sector size is 1024 (not 512)

[COLOR="Red"]Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 30400 cylinders
Units = cylinders of 16065 * 1024 = 16450560 bytes
Disk identifier: 0x0003dd81

   Device Boot      Start         End      Blocks   Id [/COLOR] System
```
5.) Snapshot gparted-1.png shows, how the gparted recognises /dev/sdc device. As half-sized actually.
6.) Then I try to create ntfs partition (cca 100GB) using gparted as is shown on gparted-2.png. The gparted has crashed.
7.) What fdisk-l listed after this crash is here (only /dev/sdc)
```
Note: sector size is 1024 (not 512)

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 30400 cylinders
Units = cylinders of 16065 * 1024 = 16450560 bytes
Disk identifier: 0x0003dd81

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Red"]/dev/sdc1               1        6374   102398278   83  Linux[/COLOR]
```
This is strange for me ...
8.) Then I've decided to go from commandline. See points 3.)- 5.) in attached fdisk-parted.txt.
9.) So my conclusion is that parted utility is not able to handle disks with logical sector size != 512, or there is something wrong with Samsung S2, but I'am not sure where the problem could be.
10.)Please check the point 5.) from attached file. After parted crashed, the partition was created only for first half of the disk and then parted crashed.
I don't know what happened to your disk when you originally tried to set it up. If all else fails you will need to use either  A Samsung hard disk tool to wipe the entire drive or something like [dban]("http://www.dban.org/") to do so.
 Your sector size seeems to be the problem. it should be 512. You have double that. That may be why only half your disk's space is available. I think when you used fdisk you messed it up.

---

### Post by macalaki on 2009-12-09
Hi, wiping the disk did not help. I'am not able to change sector size to 512B on this disk. But I do not understand why sector size != 512 is not supported in Linux.

---

### Post by presence1960 on 2009-12-09
> **macalaki said:**
> Hi, wiping the disk did not help. I'am not able to change sector size to 512B on this disk. But I do not understand why sector size != 512 is not supported in Linux.

it is supported in Linux, you are the one who probably changed it using the command line fdisk. All my 3 internal disks and my external disk are 512. That includes Ubuntu Karmic & Sabayon 5.0

 Open a terminal and run ```
man fdisk
``` There is material in there with commands on how to change the sector size.

Next time it might be best to use gparted to do partitioning...hopefully lesson learned.

---

### Post by macalaki on 2009-12-10
Unfortunately, you are not right. The problem is that mentioned Samsung S2 disk allows min sector size 1024B. Probably the firmware does this. So no utility (maybe from Samsung) is able to change it. The format command in Win at least informs that the minimal possible sector size is 1024.

---

### Post by presence1960 on 2009-12-10
> **macalaki said:**
> Unfortunately, you are not right. The problem is that mentioned Samsung S2 disk allows min sector size 1024B. Probably the firmware does this. So no utility (maybe from Samsung) is able to change it. The format command in Win at least informs that the minimal possible sector size is 1024.

That is strange. I went to Samsung's site and read the entire manual for that disk. It makes no mention of that fact, If I were you I would call their customer support and find out about all this. I will continue to use seagate 100% as I have for many years. I have never had a problem with a Seagate HDD nor has one ever died on me- ever! Good luck, I hope you get this squared away. Call Samsung maybe they can help you.

---

### Post by PomCompot on 2009-12-22
Hi,

I got exactly the same problem than yours ([http://forum.ubuntu-fr.org/viewtopic.php?pid=3079676#p3079676](http://forum.ubuntu-fr.org/viewtopic.php?pid=3079676#p3079676)).

No solution found until now. I use the entire disk :'-|. So bad.

I have read plenty of forums and my conclusion is that neither fdisk, nor parted support correctly the 1024 sector size. I have no other disk of that sort for testing, but it seems clear.

It’s frustrating because this disk is quite a good one: affordable, nice looking, small, with a case to protect it. Would like to have both data and a bootable Ubuntu on it like on my previous one.

---

### Post by phdn on 2009-12-22
I am not sure why you would want to install Ubuntu on an external HDD. The installation can only run on one computer anyway so it would be better to install it on the internal HDD (re-sizing the Windows partition if necessary during the install process) and use the external USB drive for storing data.

It may be possible to install Ubuntu on an external USB drive but it is a bit like trying to put a round peg into a square hole.

---

### Post by presence1960 on 2009-12-22
> **phdn said:**
> I am not sure why you would want to install Ubuntu on an external HDD. The installation can only run on one computer anyway so it would be better to install it on the internal HDD (re-sizing the Windows partition if necessary during the install process) and use the external USB drive for storing data.

It may be possible to install Ubuntu on an external USB drive but it is a bit like trying to put a round peg into a square hole.

You are correct that it is better to install to an internal disk, but so far from the truth that installing to an external is hard, like trying to put a round peg into a square hole.

Installation to an external for Ubuntu is basically the same as to an internal disk. Your machine of course must be able to boot from USB, you want to put GRUB on MBR of the external disk so it is not necessary to have the external plugged in to boot whatever you have on your internal disk. I have personally helped many on here install Ubuntu to an external disk with success. The problem in this thread is the sector size on the external is set to 1024 not 512. This is the sticking point as almost every disk I have ever seen or used is set to 512 by default. And the Samsung external disk is not able to be changed to 512 so the OP is out of luck unless someone else knows of a workaround.

Don't be telling others installing Ubuntu to an external is not "good" or "hard" for you do not know the reason(s) they need to do that. The fact is that it is fairly simple to do and runs rather successfully if your hardware cooperates. This is the first instance I have come across that hardware is preventing the install to external disk.

---

### Post by PomCompot on 2009-12-23
Moreover, with the USB disk creator, you can create a live usb which is not specific to a PC. Very convenient.

But, it's not the point of this thread, and I hope so much a solution to our problem.

---

### Post by todorkichukov on 2010-03-10
Try this:
> Instead of using fdisk you should use cfdisk

#cfdisk /dev/sdb
create a file system then you can use

#mkfs.ext3 /dev/sdb1
This will create a file system with ext3.

Hope this helps some of you.

Source:
[http://www.complife.com.au/?p=194]("http://www.complife.com.au/?p=194")

---

### Post by PomCompot on 2010-03-10
fdisk or cfdisk: same problems :( The problem is not in making only one huge partition, the problem happens when trying to make multiple partitions.

---

