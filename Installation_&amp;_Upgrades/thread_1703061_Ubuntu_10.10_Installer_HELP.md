---
title: "Ubuntu 10.10 Installer HELP"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by TheVlogcreation on 2011-03-08
**When Installing "Ubuntu 10.10" it freezes when I press "Forward" on the "Preparing to install Ubuntu"?**


Im using a usb flash drive to install it.. I have tried a million times but it never work

PLEASE HELP

---

### Post by TheVlogcreation on 2011-03-08
When Installing "Ubuntu 10.10" it freezes when I press "Forward" on the "Preparing to install Ubuntu"? Im using a flash drive

---

### Post by Hedgehog1 on 2011-03-08
TheVlogcreation,

Not a lot to go on here, so lets gather some info and see what we can see.  We need two things:

1) Please let us know if you are doing a 'use the whole drive' or installing Ubuntu 'Side by Side' with windows.

2) Lets get a look at the info about your hard drive(s).

Please boot up on the Ubuntu USB and select the 'try' option.

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

### Post by Iowan on 2011-03-08
Threads merged...

---

### Post by djshortsleeve on 2011-03-08
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders
Units = cylinders of 1892 * 512 = 968704 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           5        4138     3909696    c  W95 FAT32 (LBA)

What does this mean?

---

### Post by TheVlogcreation on 2011-03-09
The Whole Disk and 
[FONT=monospace]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006b88e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       29637   238053376   83  Linux
/dev/sda2           29637       30402     6142977    5  Extended
/dev/sda5           29637       30402     6142976   82  Linux swap / Solaris

Disk /dev/sdc: 8000 MB, 8000110592 bytes
247 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007593f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1020     7810109    c  W95 FAT32 (LBA)
[/FONT]

---

### Post by djshortsleeve on 2011-03-09
Looks like me and VLOG are in the same situation?  I am guessing a very NOOB situation...

---

### Post by Hedgehog1 on 2011-03-09
> **djshortsleeve said:**
> ubuntu@ubuntu:~$ sudo fdisk -l
 
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
 
[COLOR=red]**Disk /dev/sda doesn't contain a valid partition table**[/COLOR]
 
Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders
Units = cylinders of 1892 * 512 = 968704 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18
 
Device Boot Start End Blocks Id System
/dev/sdb1 * 5 4138 3909696 c W95 FAT32 (LBA)
 
What does this mean?
 
djshortsleeve,
 
Your situation is that your first 640 gig hard drive has no partitions laid out at all. It is completly blank.
 
Please reinstall, choose the manual install method and make 3 parititons:
/dev/sda1 20 gigs: ext4 '/'
/dev/sda2 5 gigs: Swap
/dev/sda3 'the rest of the disk space' ext4 '/home'
or (/dev/sda3 **130 gigs** if 'the rest of the disk space' fails)
 
 
***The Hedge***
 
:KS

---

### Post by Hedgehog1 on 2011-03-09
> **TheVlogcreation said:**
> The Whole Disk and 
[FONT=monospace]ubuntu@ubuntu:~$ sudo fdisk -l[/FONT]
 
[FONT=monospace]Disk /dev/sda: 250.1 GB, 250059350016 bytes[/FONT]
[FONT=monospace]255 heads, 63 sectors/track, 30401 cylinders[/FONT]
[FONT=monospace]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT]
[FONT=monospace]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=monospace]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=monospace]Disk identifier: 0x0006b88e[/FONT]
 
[FONT=monospace]Device Boot Start End Blocks Id System[/FONT]
[FONT=monospace]/dev/sda1 1 29637 238053376 83 Linux[/FONT]
[FONT=monospace]/dev/sda2 29637 30402 6142977 5 Extended[/FONT]
[FONT=monospace]/dev/sda5 29637 30402 6142976 82 Linux swap / Solaris[/FONT]
 
[FONT=monospace]Disk /dev/sdc: 8000 MB, 8000110592 bytes[/FONT]
[FONT=monospace]247 heads, 62 sectors/track, 1020 cylinders[/FONT]
[FONT=monospace]Units = cylinders of 15314 * 512 = 7840768 bytes[/FONT]
[FONT=monospace]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=monospace]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=monospace]Disk identifier: 0x0007593f[/FONT]
 
[FONT=monospace]Device Boot Start End Blocks Id System[/FONT]
[FONT=monospace]/dev/sdc1 * 1 1020 7810109 c W95 FAT32 (LBA)[/FONT]

 
TheVlogcreation,
 
Lets have you do the same thing, please.
 
Please reinstall, choose the manual install method and make 3 parititons:
/dev/sda1 20 gigs: ext4 '/'
/dev/sda2 5 gigs: Swap
/dev/sda3 'the rest of the disk space' ext4 '/home'
or (/dev/sda3 **130 gigs** if 'the rest of the disk space' fails)
 
In both your cases, I think the 137gig limit on the first partition on some hardware is stopping you both. By giving you a 20 gig '/' (root) partition, we get past this.
 
***The Hedge***
 
:KS

---

### Post by djshortsleeve on 2011-03-09
How do you do a manual install?

---

### Post by TheVlogcreation on 2011-03-10
I cant because when I click "forward" the Installers freezes

---

### Post by mörgæs on 2011-03-10
Exactly where does it freeze? At the step where you entered your user name?

---

### Post by djshortsleeve on 2011-03-10
Mine freezes after I hit forward on the page where you can check off to allow third party software etc.
 
I think we found the problem - the unpartitioned hard drive.
 
I will partition with Windows 7 and then try to install.

---

### Post by TheVlogcreation on 2011-03-10
Okay 1 step Choose your Language 
2nd step make sure you are connected to the Internet and have 2gbs  
and when I click forward on the 2nd step it freezes

---

### Post by millard859 on 2011-03-10
Please excuse me if any of this message sounds stupid, as I am brand new to ubuntu. I installed Ubuntu Netbook yesterday, and things were going great. when i booted this morning i was getting all sorts of errors. seeing as something was obviously wrong, i grabbed my usb that i had used to install, ran live, and tried to re install.... i am getting to the same point and the installer freezes. i did the sudo disk -l command and got the following:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f2914

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30020   241127424   83  Linux
/dev/sda2           30020       30402     3068929    5  Extended
/dev/sda5           30020       30402     3068928   82  Linux swap / Solaris

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders
Units = cylinders of 6960 * 512 = 3563520 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1126     3915752    b  W95 FAT32


like i said, new to ubuntu and don't know if my problem is the same as with the other users who are freezing, but any advice would be great.

thanks

---

### Post by pearce007 on 2011-05-05
I got the same problem when I am trying to install Ubuntu:

I have tried running Ubuntu of the DVD and it works fine, but when it comes to me installing Ubuntu I get past the select language page and to the:

Preparing to install Ubuntu
For best results, please ensure that this computer:

(tick) has at least 4.4 GB available drive space
(tick) is plugged into a power source
(tick) is connected to the internet

I then press the 'Forward' button and thats as far as it gets, just the loading circle with no progress!

I have opened terminal and done the fdisk and these are the results:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb8357863

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           1       59783   480201724   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           59783       60802     8182812   42  SFS
Partition 3 does not end on cylinder boundary.
ubuntu@ubuntu:~$ 

Does anyone know what I need to do next? :confused:

---

### Post by mörgæs on 2011-05-05
Have you tried installing using the alternate ISO?

[www.releases.ubuntu.com](www.releases.ubuntu.com)

---

