---
title: "Win7 partition lost after Ubuntu re install"
date: 2015-03-18
forum: Installation &amp; Upgrades
---

### Post by mohammed-moumen on 2015-03-18
Hi guys

don't lough on please!

I really messed up this time and it seems that everything i am doing is wrong!

I had 2 partitions with dual Ubuntu with what it seems Ubuntu 14.04 as master if the term is correct! Then I messed up with a command line that was supposed to solve my RAM problem (i was genius because that command line touched the kernel :) ) and it last with the famous error (for the ubuntu partition) : kernel panic ... no working init found ==> after lot of forums searching I end up with the decision to re install Ubuntu in my Dell laptop (I thought it will automatically install it in its partition but how genius was I when not paying attention to the "something else" option) ===> the result is like that :

- I installed sucessfully Ubuntu 14.04 64 bits

- reboot

- guess what : No Win7 partition!!! that is so frustrating guys! It seems I lost it this time!

any help please, I am about to cry :(

---

### Post by pmi2 on 2015-03-18
Perhaps you can supply a little more information, and then someone can give you direction on how to proceed.  If Ubuntu is booting correctly, you could open the terminal, and examine what partitions are actually on the disk.  For example,
> sudo fdisk -l
this will show some general information about the disk drive, and just below that, a short list of partitions and what they contain, in the form of a table.  

If you are lucky, it will also show the windows partition, if you did not erase/replace it during the install.

---

### Post by mohammed-moumen on 2015-03-18
thank you pmi2 for your answer, that is the return of the command line you gave me :

moumen@moumen-Inspiron-5537:/$ sudo fdisk -l 
[sudo] password for moumen: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/mapper/ubuntu--vg-root: 995.2 GB, 995228647424 bytes
255 heads, 63 sectors/track, 120996 cylinders, total 1943805952 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 4169 MB, 4169138176 bytes
255 heads, 63 sectors/track, 506 cylinders, total 8142848 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

---

### Post by fantab on 2015-03-19
Did you chose to encrypt the partitions? or Did you use LVM? or both?
Anyway, since
> WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Post the output of :
```
sudo parted -l
```

However, it seems you've overwrote your Windows install, which was probably Win8 with UEFI install, because Windows won't boot from a GPT disk in MBR/BIOS/Legacy mode.
If you have any data to rescue from Windows then stop using Ubuntu from HDD and use Live Ubuntu... Try [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec").
There are other Windows tools that can help you recover lost NTFS partitions, like [Mini Tool]("http://www.minitool.com/free-tools/minitool-partitionrecovery.html"), which you can try and see if it helps.

---

### Post by pmi2 on 2015-03-19
From the output of fdisk, the two partitions created during Ubuntu install are the only two left on the disk now.

so, as posted above, you have to decide if you want to try to recover any data from the previous Windows7 install, or just start over.

If you decide to start over, installing Windows 7 first, and Ubuntu second, look at the Ubuntu install options carefully and install Ubuntu alongside Windows.  

There is probably no reason to use LVM on a single disk with a dual boot alongside of Windows, so you can safely say no to LVM next time.  Same thing with encryption, if you not sure that you need it, don't select it during installation.

edit:

When you installed Ubuntu, you may have run into problems with UEFI 
(if your machine has that, instead of a conventional BIOS).  
Those issues are described in great detail in this post:

[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by mohammed-moumen on 2015-03-19
> **pmi2 said:**
> 
edit:

When you installed Ubuntu, you may have run into problems with UEFI 
(if your machine has that, instead of a conventional BIOS).  
Those issues are described in great detail in this post:

[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

Here is the return of the command line :

moumen@moumen-Inspiron-5537:~$ sudo parted -l
[sudo] password for moumen: 
Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size   File system  Name  Flags
 1      1049kB  538MB   537MB  fat32              boot
 2      538MB   794MB   256MB  ext2
 3      794MB   1000GB  999GB                     lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 995GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  995GB  995GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 4169MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  4169MB  4169MB  linux-swap(v1)



I am asking please what is the UEFI mode? because when I boot my laptop (Dell Inspiron 5537 amd 64 bit) there is something like that as an option which I don't understand?
Then, did I lost my Win7 partition for good now? If so, I have to reinstal resize and all that stuff again? but If I have to reinstall my Windows partition I do't want to go through this kind of problem again, so how should I do? I think (please correct me) I have to avoid the dual boot and create different partition which are independant to each other and which are not affected in no way by the other's failures so how to do so?

Thanx in advance guys you are being so helpful!

P.S : yes I think I selected LVM but not encryption ! I thought that LVM selecting would give me the option to choose where to put my Ubuntu (under dev/sda1) and which It didn't so I was sitting there watching my mistake :D

---

### Post by fantab on 2015-03-19
Simply put, UEFI is a replacement for BIOS. UEFI need  {GUID Paritoin Table}GPT parittions while BIOS needs MBR  'msdos' partitions.
It is good idea to use UEFI if its available... however no volcano will errupt any time soon if you don't.

LVM on the other hand is complicated for a new Linux user, it call Logical Volume Management... instead new users should stick to the default ext4 filesystem on Ubuntu and many other distros.

If you have no data to rescue then... boot Ubuntu from USB/DVD and "Try ubuntu"... open Gparted -> Devices -> create new partition table -> defaut=msdos : advanced=GPT... 
If you want to use UEFI then go with GPT, if not stay with the default, 'msdos'.
After a new partition table is created [ALL DATA ON THE HDD WILL BE LOST] you will be left all unallocated space, no partitions.
Exit Gparted and Exit Ubuntu.
Gparted Tutorial: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Reinstall Windows and create Partitions using Windows Disk Managment during install. For Ubuntu install leave unallocated space.
Once Windows is installed and all set up, boot Ubuntu DVD/USB and Try Ubuntu -> open Gparted.
From the unallocated space make your self at least two partitions one for ubuntu '/' and one for swap. Ideally you should have three:
25Gb ext4 for ubuntu '/'
???Gb ext4 for ubuntu /home (to store your personal data)
2-4Gb linux_SWAP.
This [Wiki]("http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html") could be useful.

---

### Post by pmi2 on 2015-03-19
Unless you want to try to recover files from your old Windows installation first, you will have to start over.  You are not the only one, there are lots of posts from other people, UEFI related bug reports, install and restore issues, going back years.  Leave some unallocated space on your disk for Linux, and some for a common Data volume to be used by both Windows and Ubuntu.

You can either turn off UEFI if you have that option in your BIOS Setup/Boot menu (simpler), or you can install BOTH Windows AND Ubuntu in EFI mode (more complicated).  To do the latter, you will have to do some reading.

LVM will not help you in any way during installation, it is a way to manage disks and volumes on complicated systems, like servers, workstations, and such.  LVM (Universal Volume Management) dates back to 1998, when a lot of people had computers with multiple small disk drives, SCSI controller cards, and Tape drives, mostly on servers, workstations and such.  We used to call systems like that "disk farms", because it seemed like every few weeks a new disk or set of RAID disks seemed to just appear, LOL.  

LVM has a lot of neat functions, but for the most part, you have to have multiple disks to make use of it, and its basically a relic that survives for the convenience of a few system administrators, and to make the life of the average user more difficult.  It's old, and I mean really, REALLY old...  older than Pentium 4 computers, older than Windows XP.

UEFI was a replacement for BIOS, it resides on your motherboard, and is part of the computer "firmware".  If you run Windows 7, you can safely disable it in the BIOS setup, the Boot menu. (I am not sure about Windows 8)  By the time Windows 10 ships with most new computers, it may be indispensable, but for now, if you have the option, you can turn it off.

Best of luck, :)

---

### Post by mohammed-moumen on 2015-03-19
thank you guys, It was really helpful!
I am going to let this thread opened while waiting for my laptop to be get back from the SAV (before I wrote this thread I had changed my motherboard because of some problems and now the same problem has appeared)! It seems that these days I am unfortunate!
So thank you guys, and I will get back to you as soon as I can!
best regards!

---

