---
title: "i can't delete partition"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by ghqtsy on 2010-07-31
Hi all, 

Every time when I boot, the screen shows : " error: hd0,1 out of disk" then shows me a "grub rescue" prompt. 
so i did reinstall,but when i deleted all partitions, it show me :(

warning:re-reading the partition table failed with error 16: device or resource busy.
the kernel still uses the old table .the new table will be used at the next reboot or after you run partprobe.

then i exec  partprobe, shows:(


warning: partition 5 on /dev/sda could not be modified, probably because it is in use. as a result, the old partition will remain in use
until after reboot.you should reboot now before making further changes.


To provide more information, I have the following information printed :

Disk /dev/sda: 61.6 GB, 61633732608 bytes
255 heads, 63 sectors/track, 7493 cylinders, total 120378384 sectors
Units = sectors of 1 * 512 = 512 bytes
I/O size (minimum/optima): 512 bytes / bytes
Disk identifier: 0x000cd72b

device    start     end       blocks   id system 
/dev/sda1 2048      115372031 57684992 83 linux
/dev/sda2 115374078 120377343 2501633  5  extended
/dev/sda5 115374080 120377343 2501632  82 linux swap


As you may see too, I have found that the partition /dev/sda1 started at '7182' instead of '1'. I think this is where the problem is, however, I just don't know how to fix it. When I use 'Gparted', I see there is a 1mb unallocated space sits in the beginning of the disk, if this is the case, why not "7182"? Is this a indicator that the "1~7182" is marked as bad sector, so that the ubuntu automatically added a padding 7182right after it? Is this mean my 10GB hard disk is bad? BTW, I have tried to move the partition to the beginning of the disk, but has no luck to fix my problem.

Any comment is welcome, thanks!

---

### Post by Rubi1200 on 2010-07-31
Hi,
the best thing to do is boot the computer with the LiveCD and then go to GParted. Then take a screenshot and post it here (find the screenshot application under Applications > Accessories).
 
However, one thing I can say is that the error messages seem to indicate that you tried formatting partitions that were still in use (mounted).
 
In general, it is advisable to format partitions from a LiveCD, making sure that the partitions are unmounted (not in use; indicated in GParted by a key symbol next to the partition in question).

---

### Post by ghqtsy on 2010-08-01
thanks, Rubi1200

i took 2 pictures,one is before i delete partitions, the other is when i saved screen show error message.


[ATTACH]165166[/ATTACH]

[ATTACH]165167[/ATTACH]

can you know what's error with my pc from the picture?

---

### Post by Rubi1200 on 2010-08-01
The first screenshot seems normal to me. The only thing I can think of is that there is some problem with the disk; indicated by the input/output error.
 
One more thing I would try is to first delete the swap partition, let it complete.
 
Then, delete the extended partition and see what happens (if there are error messages or not).
 
Next, delete the 1MB partition and finally the primary partition (sda1).
 
The reason I suggest you do each stage separately is so we can see if there are other error messages that might occur.

---

### Post by oldfred on 2010-08-01
I do not think your problem has to do the with partition layouts. But see this to see if yours is one of the systems that may have problems. Starting at sector 2048 is now the standard and has been the standard for Vista & 7.

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Partition%20alignment%20changes%20may%20break%20some%20systems)
By default, Ubuntu 10.04 LTS aligns partitions on disk to 1 MiB (1048576 bytes) boundaries.

---

