---
title: "LVM Root Partition Missing"
date: 2014-02-17
forum: Installation &amp; Upgrades
---

### Post by J._D._Trouteater on 2014-02-17
I broke my root partition and now I'm stuck. 

When try to boot in recovery mode I get the initramfs prompt after
ALERT! /dev/mapper/ubuntu--vg-root does not exist.  Dropping to a shell!

(This all happened after I used gparted to resize partitions, which was necessary in order to upgrade to the new Ubuntu because there wasn't enough space on my boot partition).

Anyway, I'd like to recover this system without having to wipe the whole drive, but I'm stumped for what to do next. I have a hunch what I have to do next is tell fstab where the new root partition is via the live USB stick (which I have) but I'm not sure how exactly to do that. Any help would be appreciated.

---

### Post by Bashing-om on 2014-02-17
J._D._Trouteater; Hi ! My welcome to the forum.

This situation may or may not be real real real bad.
> 
 /dev/mapper/ubuntu--vg-root does not exist. Dropping to a shell!

Did you encrypt your file system(s) ? -> then all bets are off !

ELSE:
Show us how the "land" lays, so we get an idea of what we are working with, and what there is to do.
Boot from the liveUSB ->
Post back to us the outputs - between code tags - of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

If there is something to work with, then we will see what can be done.
A screen shot of the disk drive from the liveUSB -> GParted would also be very nice.

maybe yes
[INDENT][INDENT]but probably not so yes
[/INDENT][/INDENT]

---

### Post by J._D._Trouteater on 2014-02-17
[FONT=courier new]ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   625142447   312571223+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 1027 MB, 1027416576 bytes
32 heads, 62 sectors/track, 1011 cylinders, total 2006673 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00056334

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     2005823     1002881    c  W95 FAT32 (LBA)

ubuntu@ubuntu:~$ sudo parted -l from live cd
Model: ATA ST320LT012-9WS14 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  221MB  220MB  fat32              boot
 2      221MB   456MB  235MB  ext2
 3      456MB   320GB  320GB  ext4               lvm


Model: SanDisk U3 Cruzer Micro (scsi)
Disk /dev/sdb: 1027MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  1027MB  1027MB  primary  fat32        boot, lba

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA ST320LT012-9WS14 (scsi)
Disk /dev/sda: 625142448s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start    End         Size        File system  Name  Flags
 1      2048s    432127s     430080s     fat32              boot
 2      432128s  890879s     458752s     ext2
 3      890880s  624936959s  624046080s  ext4               lvm

ubuntu@ubuntu:~$ lsblk -f
NAME   FSTYPE LABEL MOUNTPOINT
sda                 
&#9500;&#9472;sda1              
&#9500;&#9472;sda2              
&#9492;&#9472;sda3              
sdb                 
&#9492;&#9472;sdb1              /cdrom
loop0               /rofs
[/FONT]

---

### Post by Bashing-om on 2014-02-17
J._D._Trouteater; Welp.
Not looking good for the home team.

> 
3 456MB 320GB 320GB ext4 lvm

lvm == Logical Volume Management (??)
Or I ask again is this a case of encrypted file system ?

I see no indication of a separate /boot partition. So, no telling what might have happened when you sicked GParted on a non-existent partition.

lvm bothers me a lot as I can not cope with it .. I would like to try and mount that ubuntu (ext4) partition,  However, I have no idea how to overcome lvm.

[INDENT][INDENT]sometimes, I just do not know
[/INDENT][/INDENT]

---

### Post by J._D._Trouteater on 2014-02-17
I really don't think it's encrypted. I don't remember encrypting it. I even had it set up to login to my account without a password by default since I'm the only person who ever uses this computer. So, unless I'm forgetting something, it's not encrypted.

According to gparted there are four partitions. 
/dev/sda1, which is fat32 and flagged as boot
/dev/sda2, which is ext2 and flagged as nothing
/dev/sda3, which is ext4 and is flagged as lvm
and 
unallocated

Thank you for your help.

---

### Post by Bashing-om on 2014-02-18
J._D._Trouteater; OK ,

Let's try this and see if we can access your /home directory and the /boot directory.
Boot the liveUSB to a terminal:
```

sudo mkdir /mnt/work
sudo mount /dev/sda3 /mnt/work
ls -la /mnt/work/home/<your_user_name>/
##how about ?##
ls -la /mnt/work/boot/

```
when done one must ReMemBer to UNmount the partition that was manually mounted, else file system damage will result !
```

sudo umount /mnt/work

```

If you are able to access these directories from the liveUSB, there is great hope to salvage this situation.

[INDENT][INDENT]we be try'n
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-02-18
I do not know LVM, but you do not use gparted with LVM. LVM is logical partitions that may overlap multiple physical partitions underneath or even on multiple drives. It lets you have one large partition where several physical partitions may exist. But then you cannot modify physical partitions easily.

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)

---

### Post by J._D._Trouteater on 2014-02-18
[FONT=courier new]ubuntu@ubuntu:~$ sudo mkdir /mnt/work
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt/work
ubuntu@ubuntu:~$ ls -la /mnt/work/home/
ls: cannot access /mnt/work/home/: No such file or directory
ubuntu@ubuntu:~$ cd /mnt/work/
ubuntu@ubuntu:/mnt/work$ ls
empty_file  lost+found

[/FONT]

---

### Post by Bashing-om on 2014-02-18
J._D._Trouteater; Hey ,

You need to complete the path to "your" /home directory.
> 
ubuntu@ubuntu:~$ ls -la /mnt/work/home/
ls: cannot access /mnt/work/home/: No such file or directory

AS IN:
> 
ls -la /mnt/work/home/<your_user_name>/

Where <your_user_name> is the name you used when you installed your system, Each user on the system has their own directory under the /home directory.
As in, for my example:
"ls -la /mnt/work/home/sysop/" -> sysop is my username on my system.

Looking brighter, if you can access a /home directory and a /boot directory, MAybe maybe the "lvm" is misleading, and/or my comprehension is lacking.

[INDENT][INDENT]it is all a process of learning
[/INDENT][/INDENT]

---

### Post by J._D._Trouteater on 2014-02-18
Ah. I did use my username, I just deleted it for this post. Here's what I did:

[FONT=courier new]ubuntu@ubuntu:~$ sudo mkdir /mnt/work
ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt/work
ubuntu@ubuntu:~$ ls -la /mnt/work/home/<myusername>
ls: cannot access /mnt/work/home/<myusername>: No such file or directory
ubuntu@ubuntu:~$ cd /mnt/work/
ubuntu@ubuntu:/mnt/work$ ls
empty_file  lost+found[/FONT]

---

### Post by Bashing-om on 2014-02-18
J._D._Trouteater; Yuk,

OK, I am at a loss to help !
a) lvm is real, and the file system is encrypted, and thus no access is permitted;
b)lvm is real, management of the physical volumes is applied, and I have no idea how to access such a file system;
c) The file system is no longer in existence, and resorting to file recovery applications (e.g.testdisk) is in order.

Hopefully, ones with experience with "lvm" will see this thread and advise better.

[INDENT]there are those times
[INDENT][INDENT]I just do not know
[/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2014-02-18
Changed title, so maybe someone that really knows LVM may see it.

---

### Post by steeldriver on 2014-02-19
I don't "really know" LVM but I doubt that simply mounting the physical volume (/dev/sda3) will give access to the files - assuming that shrinking the partition has corrupted the PV metatdata it *may* be possible to restore it using pvcreate with the --uuid=XXXX and --restorefiles options followed by vgcfgrestore but I've never done it and don't feel competent to advise

---

### Post by J._D._Trouteater on 2014-03-08
Thanks for the help. I tried a lot of things and finally decided it was useless. I may have encrypted it and forgotten that I did it? Weird because I never had to input a password to login. There always was a problem with the size of the partition anyway. The hard drive itself is 320GB but I only ever had access to about 100 of it from within the OS and I never understood why.

Anyway I completely reinstalled everything and it all works right now. Thank you for your help.

---

### Post by Bashing-om on 2014-03-08
J._D._Trouteater; Good deal;

Thanks for the advisement and update - what you did to resolve.
There are those times that a (re-)install is the best option - but I hate when that happens. (we learn little of the cause/effect)

The good thing is that you are up and running ! Please mark this thread solved: 1st post -> thread tools. This aids others seeking a solution and as well helps keep the forum tidy.

This is ubuntu and all things are possible - a little help though goes a long way.

[INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT]

---

