---
title: "Basic help needed"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by thereid on 2010-12-04
Ok; Lets start with some basics.
What is a "/dev/sda(1,2,3,or 4)" ??

---

### Post by Quackers on 2010-12-04
> **thereid said:**
> Ok; Lets start with some basics.
What is a "/dev/sda(1,2,3,or 4)" ??

They are partition numbers on /dev/sda (usually the first hard drive).
/dev/sdb1/2/3 would be partition numbers on the second hard drive in a 2 drive system.

---

### Post by thereid on 2010-12-04
> **Quackers said:**
> They are partition numbers on /dev/sda (usually the first hard drive).
/dev/sdb1/2/3 would be partition numbers on the second hard drive in a 2 drive system.

Ok; Does "dev" mean "device"?(meaning hard drive)...and what does "sdb" mean?

I'm trying to install maverick after cluster**** upgrade (reference my earlier posts)...


I have a 120GB hard drive, most of which is allocated to Win XP (which I use most).
32.490GB is allocated for Ubuntu (Which I would like to learn...but...).

When I try to install, I get "No root file system is defined".  "Please correct this from the partitioning menu".

How do I partition this WITHOUT losing my Win XP partition???
I'm OK with overwriting any previous versions of Ubuntu..there's nothing I need to save.

Device        Type        Mount Point        Format?        Size        Used
/dev/sda1    ntfs                                                     82.8GB     unknown
/dev/sda2    fat32                                                   4722MB    4217MB    )This might be the original OEM restore drive?)
/dev/sda3    fat32                                    X             32490MB  6099MB


No root file system is defined.

Please correct this from the partitioning menu.



???  How do I do this?

---

### Post by wilee-nilee on 2010-12-04
Can you do what I asked in your last thread, asking questions is great but without some specificity we can end up with a nice doorstop.

Post the bootscript in my signature, put all the text in code tags as described in my signature as well.

We want to help but we also want to protect your setup first.;)

---

### Post by matt_symes on 2010-12-04
Hi

Sounds like a mount point for / has not been selected on the partition page when installing.

Kind regards

---

### Post by akand074 on 2010-12-04
Your sda3 looks like the partition you want to use for Ubuntu. You can do it through a manual install. Pop in the disk/flash drive you have the Ubuntu installer on. Boot into it and choose to do a manual install. This will bring you to a partitioner where you will do these steps:

1. Select that 32.490GB Drive you made for Ubuntu and delete it. Now you'll have that 32GB as "unallocated.
2. Right click the "unallocated" space and choose to edit it. Now make it's size equal to the amount of RAM you have and set it as "swap". That's all you'll have to do for that one.
3. Now with the unallocated space you have left, edit it and use all of it and set it to format as EXT4, Primary, Beginning, with mount point "/" without the quotations. The mount point is very important. 
4. That's it you can click next, confirm and install. Make sure you do not touch any of the other partitions or set anything else to format or you will lose data. You should probably have a backup of all your data anyways just in case you happen to do something wrong.

---

### Post by thereid on 2010-12-04
> **wilee-nilee said:**
> Can you do what I asked in your last thread, asking questions is great but without some specificity we can end up with a nice doorstop.

Post the bootscript in my signature, put all the text in code tags as described in my signature as well.

We want to help but we also want to protect your setup first.;)


"Post the bootscript in my signature"

I'd love to...if I had a clue what that meant.

---

### Post by Quackers on 2010-12-04
sd is the more recently used designation for "hard drive"
sda is the first hard drive (Usually)
sdb would be the second hard drive
sda1 would be the first partition (1) on the first hard drive (sda)
sda2 would be the second partition on the first hard drive (sda)
sdb1 would be the first partition on the second hard drive etc etc etc

If you have tried to install already and have had the "no root file system is defined" error message it is often caused by failing to select " / " as the mount point for the ext4 partition.

As a precaution please make sure you do not already have 4 primary partitions on your system (including recovery). If you do, don't proceed with the installation.
This problem is only usually encountered with oem installation of Windows 7, but not just then :-)

---

### Post by AlphaLexman on 2010-12-04
+1 Quackers
> **Quackers said:**
> sd is the more recently used designation for "hard drive"
but, 'sd' really means a sata connection compared to an IDE connection, which will still be a '/dev/hd[a,b][1]' entry.

---

### Post by Habeouscorpus on 2010-12-04
In her signature, there is a link called "Bootscript." She wants you to click on it, and follow the directions on the page.

---

### Post by Quackers on 2010-12-04
For the boot script
please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ToFue on 2010-12-04
each OS uses identifiers for hardware devices - in linux, all devices (hardware or virtual) are registered in the /dev folder. For parallel-ATA hard drives, the prefix 'hd' is denoted, while SATA and other Special hard drives are 'sd'.  The last letter is the order that the drive is physically installed. So /sda  means that it's your first SATA drive plugged into the motherboard, while /sdb would be the second, and so on. 

As Quackers stated,  particular partitions (logical divisions of the space on your physical disk drive) of your hard drive are the number designation, as in /sda1 or /sda2 or /sda3 - they are numbered in the order that a partition was created, and may not be listed in numerical order to the order they live on the hard drive at.

For instance, if I made three partitions on my hard drive, /sda1 /sda2 and a /sda3, then wanted to resize /sda2 to allow free space between it and /sda1, once I format the free space into a new partition, it would become /sda4.

Note that there's different partitions, noteably Primary and Logical. You're limited to the number of Primary partitions you can make on one hard disk. So before you reach the limit (if you have the need) you can make an LVM partition, which address Logical partitions within it, again numbered in order of creation..

Now the files within linux navigate through the different disks using mount points. For instance, if I put my /home folder on a different partition or disk altogether, the rest of the system needs to know how to reach it. In the installation, choosing mount points is done at the same time of partitioning. When you become familiar with the process, you can choose to set custom partition & mounting schemes.

 In windows, filesystem types are FAT, FAT32, and NTFS - in Linux, you have a lot of choices, but you'll probably want to stick to ext3 (a very few programs arn't compatible with using ext4 yet - Wiki and Google are your friends). File systems are just the method an OS uses to write and read from the partition, along with other enhanced features that the OS can take advantage of, but every useable partition must be formatted with a filesystem.

 A common, basic method is to create three partitions intended for the linux system. After choosing how much disk space you want to dedicate to each mount point, you create a partition accordingly and format the partition to a particular filesystem. Then you choose the moint point for the partition, i.e /dev/sda1 can be assigned the SWAP partition, /dev/sda2 can be assigned the '/' or Root partition (not to be confused with the folder "/root"), and /dev/sda3 can mount "/home", which stores personal documents, user info, videos, pictures, etc, that you'll accumilate...

Hope this helps you get a jump on it!
Also see: [Logical Partitions](http://en.wikipedia.org/wiki/Logical_partition) and [Primary Partitions](http://en.wikipedia.org/wiki/Disk_partitioning)

It's a lot of new information, but it's not hard at all once you understand the 'why'
Cheers!

---

### Post by thereid on 2010-12-05
> **wilee-nilee said:**
> Can you do what I asked in your last thread, asking questions is great but without some specificity we can end up with a nice doorstop.

Post the bootscript in my signature, put all the text in code tags as described in my signature as well.

We want to help but we also want to protect your setup first.;)


Ok;  I have posted this "Results.txt" before, but here is is again.

I seem to have 3 partitions.  The first line in the select partitions table is blank...I assume it's just a header.

sda1 is 82GB...Thats my Win XP partition
sda2 is about 4700MB..maybe a recovery sector? I don't remember even though I installed this HD.  I think I "mirrored" the OEM HD.
sda3 is my Ubuntu partition 32Gb

Do I need to create an sda4 within this sda3 partition?  Seems like a waste of space, but if that's what I need to do, OK.

---

### Post by thereid on 2010-12-05
ToFue;
THANKS!  That's information I wish I had years ago.

"A common, basic method is to create three partitions intended for the  linux system. After choosing how much disk space you want to dedicate to  each mount point, you create a partition accordingly and format the  partition to a particular filesystem. Then you choose the moint point  for the partition, i.e /dev/sda1 can be assigned the SWAP partition,  /dev/sda2 can be assigned the '/' or Root partition (not to be confused  with the folder "/root"), and /dev/sda3 can mount "/home", which stores  personal documents, user info, videos, pictures, etc, that you'll  accumilate..."

Not sure I understand the need for 3 partitions for Linux.  What's the purpose of the "swap" partition, and the "/root" partition? (I'm guessing the /root partition is where the Linux code actually lives?)

---

### Post by SeijiSensei on 2010-12-05
Let's start with swap.  Operating systems need a place to temporarily store objects in memory when the demand for memory exceeds the size of the actual physical memory of the machine.  Windows uses a file in the operating system itself for this purpose.  Linux can also do this, but for performance reasons swap is usually written to a separate partition on the hard drive.  A good rule of thumb for machines with up to 2GB of memory is to make swap twice the size of memory.  As physical memory increases, the need for swap space typically declines.  On my 4GB machine, I have 2GB allocated to swap, of which only 600MB or so is currently in use.

The top of the filesystem tree, the directory called simply "/", is often termed the "root" of the filesystem.  You'll also see a directory called "/root".  That's the home directory of the "root" or administrative user.  All the ordinary users have directories under /home like /home/thereid. 

It's often a good idea to allocate a separate partition to /home.  Then if for some reason you want to reinstall the operating system, or install a new one, all the users' personal files won't be affected by the operating system change.  When the new OS is installed, you just tell it to mount the partition with the home directories under /home in the new OS.

If you navigate to the top of the file system, the directory represented as "/", you'll see these main directories:

bin - contains binaries used during boot and thereafter
boot - contains the kernel images and associated files needed to boot
dev - contains "device" files that represent things like drives, ports, the console, etc.
etc - contains the configuration files for nearly every program on the machine
home - users' directories
lib - contains binary "libraries" needed during boot and thereafter
media/mnt - places where additional resources (USB drives, network file systems, etc.) are mounted
opt - typically not used in Linux; a place to install software not provided by the distribution
proc - a special filesystem that contains information used by the operating system kernel; "cat /proc/meminfo" will show memory use, for instance
root - root's home directory
sbin - programs used during boot and thereafter; on some systems access to /sbin is limited to the root (administrative) user
srv - rather like /opt; not typically in use
sys - akin to /proc but with different data
tmp - temporary file storage available to all users
usr - all the files users need including programs in /usr/bin, libraries in /usr/lib, documentation in /usr/share, etc.
var - various directories written by root while the machine is in operation; logs in /var/logs, inbound mail in /var/spool/mail, etc.

Some people, myself included, allocate a separate partition to /boot.  That way I can have multiple operating system images that all store their kernels and associated files in the same place.  Then, during boot, I can select which operating system to use.  /boot can be really small; 256MB is usually more than enough.

---

### Post by thereid on 2010-12-05
> **akand074 said:**
> Your sda3 looks like the partition you want to use for Ubuntu. You can do it through a manual install. Pop in the disk/flash drive you have the Ubuntu installer on. Boot into it and choose to do a manual install. This will bring you to a partitioner where you will do these steps:

1. Select that 32.490GB Drive you made for Ubuntu and delete it. Now you'll have that 32GB as "unallocated.
2. Right click the "unallocated" space and choose to edit it. Now make it's size equal to the amount of RAM you have and set it as "swap". That's all you'll have to do for that one.
3. Now with the unallocated space you have left, edit it and use all of it and set it to format as EXT4, Primary, Beginning, with mount point "/" without the quotations. The mount point is very important. 
4. That's it you can click next, confirm and install. Make sure you do not touch any of the other partitions or set anything else to format or you will lose data. You should probably have a backup of all your data anyways just in case you happen to do something wrong.

akand074;
**CANADA ROCKS!!**

Your tip work great.  I hesitate to go messing about with my partitions, but I was at the end of my rope, so I followed your instructions and voila!
The only dicey part was creating the swap partition. The instructions didn't quite match the screen I saw. I had to back up & got it right.

Another satisfied customer.
THANKYOUTHANKYOUTHANKYOU!

---

