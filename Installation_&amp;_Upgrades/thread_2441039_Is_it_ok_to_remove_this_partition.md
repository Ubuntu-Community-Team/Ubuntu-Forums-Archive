---
title: "Is it ok to remove this partition?"
date: 2020-04-18
forum: Installation &amp; Upgrades
---

### Post by leejenon on 2020-04-18
Hi,

This is my first Linux (lubuntu) experience. How lovely it is just have the OS appear instantly after logging in on my Compaq! My query is that I seem to have a strange partition. My disk size is 500 GB, my O/S partition is 50 GB, but the disks are showing two partitions of 450 GB partitions. 

My install partition process was :-

First install - choose "Guide - Entire disk" - This was successful. I then decided I wanted a separate partition for the O/S, so I did a second install and chose "Guided - Resize"

But after logging in, I see that I have 2 x 450 partitions. Will it be ok to delete it partition #2?

Thanks 
Lee

---

### Post by dino99 on 2020-04-18
Cant see nor read your snapshot, but i suppose the installer have created a primary and an extended partition (as usual)

[https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu](https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu)

---

### Post by leejenon on 2020-04-18
Sorry about the snapshot, I took it with my phone. I'll take a proper screen shot. But is sounds like this may be normal. brb

---

### Post by leejenon on 2020-04-18
To be more accurate in my description I have this:-

Drive: 500 GB / Master Boot Record

Filesystem Partition 1 50 GB Ex4
/dev/sda1
Bootable

Extended Partition Partition 2 450 GB
/dev/sda2

Filesystem Partition 5 450 GB
/dev/sda5
Mounted at Filesystem root

Free Space
1.1 MB
/dev/sda
Unallocated space

Is this normal?

Thanks
Lee

I can't do proper screen shot right now.

---

### Post by ajgreeny on 2020-04-18
All absolutely normal!

Run command ***sudo fdisk -l*** in terminal and the output will probably show exactly the same start and end points for partitions #2 and #5; partition 2 is the extended partition, just a container really, and partition 5 is the logical partition inside #2, taking all the space available in that.

---

### Post by guiverc on 2020-04-18
The extended partition contains no data; it is a logical partition which has space used by partitions that exist within it. The partition shown below it in your picture contains the partition that actually uses & stored the space.

Both partitions that share the same horizontal space (extended & partition below it) are using the same space, so any data on either will be lost if you delete either (an extended partition is a logical entity created decades ago to get over certain partitioning problems, even if it created more complexity). ie. as I take your fuzzy picture & text, both sda2 (extended) & sda5 contain the same data (data stored in 5, but if you delete 2 you'll lose 5 automatically as it exists within 2).

You didn't give your release of Lubuntu, my guess is 18.04? as your picture reminds me of `gparted` and not KDE Partition Manager found in modern releases of Lubuntu.

---

### Post by leejenon on 2020-04-18
> **ajgreeny said:**
> All absolutely normal!

Run command ***sudo fdisk -l*** in terminal and the output will probably show exactly the same start and end points for partitions #2 and #5; partition 2 is the extended partition, just a container really, and partition 5 is the logical partition inside #2, taking all the space available in that.

Hi ajgreeny,

Same end but different start. also whats dfferent to my first install is that I now have a boot list gives these options *lubunti and another lubuntu. This didn't happen on my first install. This is what is leading me think I did something wrong the second time around.

Lee


[FONT=courier new]Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6ba3e75c

Device     Boot    Start    End       Sectors    Size   Id Type
/dev/sda1  *        2048      97658297  97656250  46.6G  83 Linu
/dev/sda2   97658878 976771071 879112194 419.2G   5 Exte
/dev/sda5         97658880 976771071 879112192 419.2G 83 Linu[/FONT]

---

### Post by CelticWarrior on 2020-04-18
It's practically the same and it's fine.
The difference you have now is because you somehow created an extended partition that wasn't needed but works the same way.[FONT=courier new][/FONT]

---

### Post by leejenon on 2020-04-18
> **guiverc said:**
> The extended partition contains no data; it is a logical partition which has space used by partitions that exist within it. The partition shown below it in your picture contains the partition that actually uses & stored the space.

Both partitions that share the same horizontal space (extended & partition below it) are using the same space, so any data on either will be lost if you delete either (an extended partition is a logical entity created decades ago to get over certain partitioning problems, even if it created more complexity). ie. as I take your fuzzy picture & text, both sda2 (extended) & sda5 contain the same data (data stored in 5, but if you delete 2 you'll lose 5 automatically as it exists within 2).

You didn't give your release of Lubuntu, my guess is 18.04? as your picture reminds me of `gparted` and not KDE Partition Manager found in modern releases of Lubuntu.

Hi guiverc,

My version is 18.04.4 LTS (Bionic Beaver) - I'm running on a old Compaq! So this was the x86 download on the lubuntu.net home page. I guess it's because of my hardware.

Thanks to you both for helping me learn.

Attached is a proper picture

---

### Post by leejenon on 2020-04-18
> **CelticWarrior said:**
> It's practically the same and it's fine.
The difference you have now is because you somehow created an extended partition that wasn't needed but works the same way.

Thanks CelticWarrior, I'm glad I don't have to install again.

---

### Post by ajgreeny on 2020-04-18
Great! 

You can also ignore that tiny 1.1 MB of free space at the end of the disk; creating partitions usually leaves these tiny areas untouched for some reason I don't fully understand, but which is of no consequence.

Please now mark as SOLVED from the Thread Tools menu up-top if this is solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by Impavidus on 2020-04-18
The 450GB sda5 is your root partition, the 50GB sda1 is unused (at least, by the system installed in sda5). Also, as you now see a grub menu where you can choose what system to boot, it appears that the installer detected a second OS already on your harddrive. Is there a second Ubuntu or Lubuntu in the 50GB partition? It appears that something didn't go entirely as planned.

---

### Post by ajgreeny on 2020-04-18
> First install - choose "Guide - Entire disk" - This was successful. I then decided I wanted a separate partition for the O/S, so I did a second install and chose "Guided - Resize"
I beileve this statement in your first post tells us a lot more than I noticed at first.

I think you probably firstly installed using a 50GB root partition and a 450GB /home partition, but then when you reinstalled the second time you did not point to the old root partition sda1 and re-use it as root again; doing so means you have to use the "Something Else" option when installing and specifically choose partitions for particular uses, ie, root and /home.

The image you attached in post #9 also shows that you are running Lubuntu, presumably your second installation, but also that sda1 is not mounted, so is not the OS in use.

So I believe you have two separate OSs on the disk, the first using the separate root partition, sda1, the second having just the single whole OS partition sda5.  I assume this means you see a grub menu when you boot the machine, and presumably could boot either OS if you chose Advanced from the grub menu.  Perhaps you could check that when you next cold boot and post back here what you see.
Command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-120
```will also show us what is available from the grub menu and may explain more about your now dual boot system.

---

