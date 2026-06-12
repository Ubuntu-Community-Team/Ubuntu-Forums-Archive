---
title: "Dual Boot installation Problem (Windows 7 and Ubuntu 10.10)"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by TXAaron on 2010-12-05
The problem is that I cannot install Linux onto my primary HHD. I boot into the DVD/USB (i've tried both,) hit install, choose English, hit next and it takes me to the "advanced" portion of choosing where to install Ubuntu to. It never gives me the option to install alongside another OS. I've noticed in the "advanced" installation that it doesn't even recognize my 1 TB hard drive (my primary, which I intend to partition using Ubuntu's installer.) I've also tried partitioning manually and installing to unallocated free space as well as a formated FAT32/NFTS format (I've done both.) No matter what I do, it doesn't come up. 

Also note that it wants to install Ubuntu to the DVD/USB, however I want it on the actual system.

- My system is 64-bit, I just built it two weeks ago. I had it on my last 64-bit system however I rarely used it.

---

### Post by wilee-nilee on 2010-12-05
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

This will give us the what and where things are, it is a very good tool.

---

### Post by TXAaron on 2010-12-05
From the results.txt

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
error: block: No such file or directory
error: devices: No such file or directory
error: /dev/mapper/no: No such file or directory
error: /dev/sda: No medium found
error: found: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sda no block devices found 
```

---

### Post by wilee-nilee on 2010-12-05
So that script is a little strange in that as far as you have described the setting you have not installed Ubuntu am I correct in this? It looks like the script was reading the Ubuntu cd

When you resized windows did it do a chkdsk automatically, and how did you resize it?

We want to be careful here your OS is the first thing in line so it sometimes takes some questions so it is helpful if you can answer them and if you don' understand just let us know.

---

### Post by TXAaron on 2010-12-05
> **wilee-nilee said:**
> So that script is a little strange in that as far as you have described the setting you have not installed Ubuntu am I correct in this? It looks like the script was reading the Ubuntu cd

When you resized windows did it do a chkdsk automatically, and how did you resize it?

We want to be careful here your OS is the first thing in line so it sometimes takes some questions so it is helpful if you can answer them and if you don' understand just let us know.
I have not installed Ubuntu and I am running it from the LiveCD - It doesn't recognize my hhd whatsoever. 

I used disk management to shrink Window's partition by 30GB. It didn't do a dskchk automatically, however I just ran one and it found no problems.  I originally wanted to use Ubuntu's partitioner to resize my disk, however it tries to install to the DVD instead of finding the hhd.

---

### Post by wilee-nilee on 2010-12-05
Looks like raid setup possibly I would wait for some qualified help, be very careful, and have it backed up.

---

### Post by TXAaron on 2010-12-05
> **wilee-nilee said:**
> I suspect that with the size of the HD 1 terrabyte you have a raid setup. This can be dealt with, but don't peck at it without getting a positive confirmed fix unless you have that thing backed up. I'm not familiar with raid or the fixes but others are.

I don't have a raid, Seagate Barracuda 1TB 7200 RPM

---

### Post by wilee-nilee on 2010-12-05
> **TXAaron said:**
> I don't have a raid, Seagate Barracuda 1TB 7200 RPM

Something is keeping it from being seen. How many partitions are on there now?

Does the HD show in gparted on the Live CD? If it does take a screen shot and post it.

I'm assuming that this cd is a working one that has been used before or you have checked the MD5SUM.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Thumb/cd what ever your using.

---

### Post by TXAaron on 2010-12-05
> **wilee-nilee said:**
> Something is keeping it from being seen. How many partitions are on there now?

Does the HD show in gparted on the Live CD? If it does take a screen shot and post it.

I'm assuming that this cd is a working one that has been used before or you have checked the MD5SUM.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Thumb/cd what ever your using.
There are no partitions currently. 

I'm not sure if it shows in gparted or not. How can I find out?

I haven't seen the drive at all linux side, only what is on the CD. 

And the CD does work. I installed Ubuntu to my laptop with it.

---

### Post by wilee-nilee on 2010-12-05
> **TXAaron said:**
> There are no partitions currently. 

I'm not sure if it shows in gparted or not. How can I find out?

I haven't seen the drive at all linux side, only what is on the CD. 

And the CD does work. I installed Ubuntu to my laptop with it.

Gparted is in the menu-systems-admin-gparted. On a Ubuntu install live cd @ the desktop.

If you have a windows install you have partitions, how many of those do you have?

Good the cd works, just trying to get to the heart of the matter and whether I can be of help really.;)

---

### Post by TXAaron on 2010-12-05
> **wilee-nilee said:**
> Gparted is in the menu-systems-admin-gparted. On a Ubuntu install live cd @ the desktop.

If you have a windows install you have partitions, how many of those do you have?

Good the cd works, just trying to get to the heart of the matter and whether I can be of help really.;)
As far as I can tell, I don't have any partitions, I built this system and installed Windows. No partitions.

---

### Post by wilee-nilee on 2010-12-05
I think you don't understand what a partition is; the NTFS portion that is the W7 install is a partition so are all the other space on the two other drives.

The two other drives look like a second hard drive and a thumb for the ready quick boost is this correct?

Looks to me that you have not made a actual unallocated space on the 1 terrabyte drive, you just use the W7 right click on that partition and hit shrink. It analyzes it and gives you a finite shrink size, choose accordingly.

If this doesn't make sense just let me know.

A partition is needed for any operating system, you could abstractly say a bucket wont hold water unless there is a bucket, the bucket is the partition to hold the water.

Do all this with the shrink and then boot the Ubuntu cd and it will show windows and the unallocated area, choose install to largest free space.

---

### Post by TXAaron on 2010-12-05
> **wilee-nilee said:**
> I think you don't understand what a partition is; the NTFS portion that is the W7 install is a partition so are all the other space on the two other drives.

The two other drives look like a second hard drive and a thumb for the ready quick boost is this correct?

Looks to me that you have not made a actual unallocated space on the 1 terrabyte drive, you just use the W7 right click on that partition and hit shrink. It analyzes it and gives you a finite shrink size, choose accordingly.

If this doesn't make sense just let me know.

A partition is needed for any operating system, you could abstractly say a bucket wont hold water unless there is a bucket, the bucket is the partition to hold the water.

Do all this with the shrink and then boot the Ubuntu cd and it will show windows and the unallocated area, choose install to largest free space.
I figured you meant on the one that has W7 installed. But yes if you include the other drive, I have 3. I did shrink my W7 drive but I added it back seeing as it didn't work. It wouldn't allow me to select the unallocated space as I said in the first post. I was going to use the Ubuntu installer to shrink my W7 partition however it just doesn't show up, whether there is unallocated space or not.

---

### Post by wilee-nilee on 2010-12-05
> **TXAaron said:**
> I figured you meant on the one that has W7 installed. But yes if you include the other drive, I have 3. I did shrink my W7 drive but I added it back seeing as it didn't work. It wouldn't allow me to select the unallocated space as I said in the first post. I was going to use the Ubuntu installer to shrink my W7 partition however it just doesn't show up, whether there is unallocated space or not.

Well I am stumped, read the first post but it was hard to tell what was up when your understanding of what a partition was that you had none but over 3 drives you have 5 partitions that actually say partition on them.

There are a couple of regular user that are on during the day US they may have some options for you.

I guess the biggest clue to me that something was amiss was that the boot script saw nothing, that is really unusual.

---

### Post by TXAaron on 2010-12-05
> **wilee-nilee said:**
> Well I am stumped, read the first post but it was hard to tell what was up when your understanding of what a partition was that you had none but over 3 drives you have 5 partitions that actually say partition on them.

There are a couple of regular user that are on during the day US they may have some options for you.

I guess the biggest clue to me that something was amiss was that the boot script saw nothing, that is really unusual.

Well I always figured a partition was a split from the primary "portion" of a hard drive, not including the primary itstelf.
 I now say there are 3 because I don't include my flash drive, it just happened to be plugged in when I took the screen shot. And I'm guessing that a partition is just a virtual drive no matter what, whether split or not.

 My secondary Hard Drive shouldn't be split in 2 as it shows, I never did that, I took it from my old windows 7 computer, where it wasn't split and continued to use it as storage.

---

