---
title: "Creating an exact image of a hard disk"
date: 2010-09-08
forum: Installation &amp; Upgrades
---

### Post by jpr0 on 2010-09-08
Hi everyone

Firstly, sorry if this is in the wrong section, but I wasn't sure where to put it. Since the background to my problem is kind of long winded I've split this post into two sections: 

_Short version of problem_

I have a PC that has two internal drives: one drive (drive A) is empty, and the other (drive B) has a copy of windows vista installed. At the moment the PC boots from drive A. I'd like to transfer everything from drive A to drive B, so that this new disk will boot and behave nicely and windows will still function. 

Is there any easy way to do this in ubuntu? I'm guessing I can use something like dd, but will this copy the boot sector and will I have to mess around with the partition table?

_Long version of the problem_

Today I built a new PC for my dad with two internal drives. He was previously using vista on a laptop which died a few days ago, and I'd like to install vista on one disk of the new PC, and ubuntu on the other disk. 

He has a licensed copy of Vista for his laptop, but it came as a "system restore" disk, and so I can't install vista directly onto the new PC. I have an identical laptop to his, so I took out the drive from his laptop, put it in my laptop, and did a "system restore" from the disk that came with the laptop. I then took out the drive from my laptop, and put this inside the new PC. It boots up fine, and I installed all the necessary drivers and etc to make windows work. 

Now instead of using a slow/small laptop drive inside the new PC, I'd like to be able to clone the data on laptop disk and this onto one of the bigger/faster internal drives of the new PC. How can I do this from ubuntu, so that the new drive will boot windows?

I'm fairly certain it can be done using dd, but how do I make sure the information in the boot sector (or partition table) is correct for the new drive? I'm asking this because when I put my laptop drive into the new PC initially, I had connected it as an external drive, and when I tried booting from this there was an error, something like "Invalid partition table" (I think). I figured that when I did a "system restore" on my laptop, the drive was the only drive available, so this would be HDA, or SDA in the boot record of that disk. But when I added it to a system where other drives were available, it was no longer at that same location, so the boot loader couldn't find the data it was looking for to load the system.

---

### Post by Mark Phelps on 2010-09-09
Personally, I've found Clonezilla to be a great tool for "cloning" drives and partitions.  You can get the LiveCD from distrowatch.com.

Download it, burn it to CD, boot from it (with both drives connected), and you should be able to "clone" the first disk onto the second.  The only limitation is that the second disk must be at least as large as the first.

After the cloning is complete, you will notice that the partition sizes on the new disk match the ones on the old disk.  This is what "cloning" does -- it makes an exact copy of the original.

IF the partitions on the disk are NTFS, and you're running Win7, I would boot into that and use the Win7 Disk Management utility to then resize the NTFS partitions -- instead of using GParted.

---

### Post by jpr0 on 2010-09-10
Hi, thanks for the reply. 
I just used dd in the end. If you just use

```
dd if=/dev/sda1 of=/dev/sda2 bs=2048
```

then it copies everything, including the mbr partition tables and so on. The only drawback is that it is slow if sda1 is big. In that case then I think one should shrink the system partition in windows and use dd to copy just the first partition. I couldn't be bothered with additional complications, though, it only took about an hour for an 80Gb disk in the end.

---

