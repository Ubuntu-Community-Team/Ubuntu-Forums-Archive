---
title: "Unexpected fsck inconsistency after trying to test jaunty"
date: 2009-03-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Tibuda on 2009-03-05
I have found a empty CD, and thought it would be a good idea to test jaunty to check for hardware compatibility etc. The live cd opened fine. I resized my home partition so jaunty can have 10GB, but the installer displayed an error telling the CD/DVD was corrupted. Ok, it was expected, as it is an old CD. The problem happened when I restarted the computer with intrepid. It opened a fullscreen terminal, telling me something was wrong with fsck, and to check /var/log/fsck/checkfs, or to try Ctrl+D to continue the boot. Then I typed:```
# cat /var/log/fsck/checkfs
Log of fsck -C3 -R -A -a 
Thu Mar  5 08:37:10 2009

fsck 1.41.3 (12-Oct-2008)
/dev/sda6: The filesystem size (according to the superblock) is 25866650 blocks
The physical size of the device is 23426778 blocks
Either the superblock or the partition table is likely to be corrupt!


/dev/sda6: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
fsck died with exit status 4

Thu Mar  5 08:37:10 2009
----------------
```Writed it on a paper, but when I pressed Ctrl+D everything worked fine (I did a backup, and this post). Do I have to worry? If it happens when I restart the computer, what should I do to run fsck manually?

Thanks

P.S. This is the first issue I have with Ubuntu since I started using it (more than a year, it was the gutsy release).

---

### Post by WatchingThePain on 2009-03-05
Hi,

This bit 'Either the superblock or the partition table is likely to be corrupt!' looks worrying (I would Google that).
When I got that error I ran fsck manually and it was fine.
Remember you have to run fsck on an unmounted or read only filesystem.

---

### Post by Tibuda on 2009-03-05
Thanks... Should I run "fsck /dev/sda6"? Or should I use an argument? Can I do it from the boot terminal or should I use my intrepid LiveCD?

---

### Post by WatchingThePain on 2009-03-05
To manually run fsck in ubuntu,

From a console/terminal type

fsck /dev/partition

You will need to replace /dev/partition with the device name of your root partition.

This should tell you what that is: 

mount | grep ' on / '

Also, first look at: man fsck

---

### Post by Tibuda on 2009-03-05
Thanks! I'll do it when my backup is over.

---

### Post by Tibuda on 2009-03-05
There's really something wrong...```
ubuntu@ubuntu:~$ sudo fsck /dev/sda6
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
The filesystem size (according to the superblock) is 25866650 blocks
The physical size of the device is 23426778 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

/dev/sda6 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error reading block 23429122 (Invalid argument) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? yes

Error writing block 23429122 (Invalid argument) while getting next inode from scan.  Ignore error<y>? yes

Error reading block 23429123 (Invalid argument) while getting next inode from scan.  Ignore error<y>? yes

Force rewrite<y>? 
```I guess I'll just format it again with gparted from my intrepid livecd. I already got a backup.

---

