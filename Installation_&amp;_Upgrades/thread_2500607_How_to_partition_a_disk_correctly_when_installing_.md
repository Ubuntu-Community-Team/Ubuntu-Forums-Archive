---
title: "How to partition a disk correctly when installing Ubuntu?"
date: 2024-09-06
forum: Installation &amp; Upgrades
---

### Post by vmelnikv on 2024-09-06
How to partition a disk correctly when installing Ubuntu?
I know there should be partitions:
EFI - FATF32
swap - EXT4
File system - EXT4
And the home directory - EXT4
But I don't remember the paths where these partitions should be.
And I don't know how much space to allocate for each partition. I heard that you can divide by percentage, but there are mandatory minimums.

I want to install Ubuntu 24.04 and I'm not interested in automatic installation.

---

### Post by ubfan1 on 2024-09-06
The "correct" partitioning is the one which best meets your present and future needs.  
EFI -  Default seems to have moved up to 1GB from 300MB (on Ubuntu Desktop 24.04). Seems a bit excessive to me, but space is generally cheap. Now if you have only 8GB total storage, you might pare that way down, 100MB or less.
Swap - no filesystem here, and no partition needed either unless you hibernate. Possible to use a swapfile (today's default) even for that, but involves setting up the block offset of the swapfile somewhere.
Root -ext4 Depends upon what you install, and how much trouble you want to take to ensure the bulk of apps go elsewhere. When game downloads can be 70GB+, you don't want those cluttering up root. I use 25GB for testing, pretty empty, 50GB was my normal for years but turned out to be too small for what I do. 100GB now, future...?
home -- ext4 but  should be just a data partition with space for your personal files. "home" as in /usr/home/<username> contains many hidden "dot" files which configure system specific apps, so trying to mix that across systems is a really bad idea. Just use links from your normal home to the datastorage.

Just my opinion, and worth every penny you paid for it. ;^)

---

### Post by vmelnikv on 2024-09-06
Are there any official recommendations and system requirements?

---

### Post by yancek on 2024-09-06
Minimum and recommended requirements are listed at the page from the link below.   Swap is not ext4 and the current Ubuntu will create a swap file rather than a swap partition.  The link below recommends 25GB for the / (root filesystem) partition but other partitions depend upon the size of your drives and space available.  I don't know what 'paths' you are referring to, did you mean mount points?   You should have choices in the Installation Type windows if you use the manual installation method. 

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by vmelnikv on 2024-09-06
I wrote it a little wrong, the requirements are not for the hardware, but for the disk partitions.

---

### Post by oldfred on 2024-09-06
Are you dual booting or just installing to one drive.
What is drive size?
I use totally different sizes if installing to a 128GB flash drive as opposed to a 1TB SSD.

Now Ubuntu uses a lot of snaps. And they can take a lot of space. Have seen a user with 20GB just in snaps.
I now use Kubuntu and delete all snaps. / (root) is using 16GB of my 30GB partition. That includes /home (but only hidden configuration files), but I have all data in separate data partition(s). 

If new user & smaller space best to just use / (root) as one larger partition. Then you do not have to manage sizes of partitions in case one gets full and other has lots of extra space. Once you have a better idea of your usage, then you can consider separate partitions.
Most systems are UEFI, so an ESP, FAT32 and / (root) ext4 are all that are required.

---

### Post by TheFu on 2024-09-07
How to partition is a judgement call.  Probably best to do a default install and see what that creates first.  It is less than 15 minutes of your time. Which file system(s) you use can matter greatly as well. Some include volume management and more advanced capabilities which are both more complex and more flexible.

Only you can decide is the extra complexity that any specific partition scheme provides is worth the extra hassle.

Over the decades, people have posted their disk layouts in these forums many times. Some with explanations.  Have you looked at those?

To help, use this command to see the different layouts.
```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```
That will work with most file systems, but it does misrepresent storage in some volume managers like ZFS and BTRFS. Still, it is the best command I know to see an overview.

I should say that I've never, not once, had my initial system layout be perfect for more than a year.  For this reason, I switched to using LVM because it doesn't require me to be perfect on the initial layout.  But it does add complexity for that extra flexibility.

Good luck.

---

