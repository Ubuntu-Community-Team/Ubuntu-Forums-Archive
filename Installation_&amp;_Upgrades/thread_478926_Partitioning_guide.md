---
title: "Partitioning guide?"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by Scooter7 on 2007-06-19
Hi, could someone give me a step-by-step guide to partitioning my drive for Ubuntu 7.04?   What I want to do is:

[LIST=1]
[*]Start the install, and work my way to the partitioning step
[*]Click Manual.
[*]Now I'd like to partition my 500 GB external drive so that I have something like 20GB for Linux - the rest is for Windows.
[/LIST]


A while back I was told to do something like this:

> **Originally posted by Wim Sturkenboom** - 
create new partitions for swap (2x memorysize with a max of 1GB), root (/; with so much space I suggest something like 20GB)) and home (/home; whatever you feel like).   I suggest you also create a fat32 partition for data exchange in case of a dual boot scenario (quite likely when you have an external HD for Ubuntu and as you mentioned windows)

So I'd like to know how to do that via the manual partition step of the installer.

Thanks,

---

### Post by louieb on 2007-06-19
live cd partitioner is based on GParted. Here the best guide I've found [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")

---

### Post by Scooter7 on 2007-06-19
Thanks, louieb - but that's not what I'm looking for, sorry. #-o

Rather, I'd like it if someone could tell me how to carry out this operation:

> **Originally posted by Wim Sturkenboom - **
create new partitions for swap (2x memorysize with a max of 1GB), root (/; with so much space I suggest something like 20GB)) and home (/home; whatever you feel like). I suggest you also create a fat32 partition for data exchange in case of a dual boot scenario (quite likely when you have an external HD for Ubuntu and as you mentioned windows)

I semi-understand how the partitioner works, so I don't need documentation on Gparted.

Just need someone to show me how to manually create the partitions for Ubuntu. :)

---

### Post by gauravp55 on 2007-06-20
Ok so you wanna keep 20 gigs for Linux. So what you can do is this:

1> Run Gparted and it'll show you the existing partitions and the free space on your HD.

2> You can choose the free space to create partitions as you wish.You need to enter the desired partition size in Megabytes and you need to mention the file system type as well as the mount point.

3> Remember to select **ext3** as the file system type for your root partition.Mount point is** /** .You could allocate about 8 GB or more for your root partition. I think 10 GB should be more than sufficient.

4> Allocate about a GB for SWAP Partition

5> You could then create a Home Partition and a Fat32 shared partition between Ubuntu and your other OS. 

6> Your done!!

---

### Post by Scooter7 on 2007-06-20
Okay, thank you, gauravp55 - just one more question, is a /home partition necessary for the install?   And I imagine I set '/home' as the mount point?   What is 'home' for, exactly?   Sorry for all these questions. :p

And, I've seen other Linux partition jobs before - not done them, mind you - and I noticed that they usually have a extended partition, then the swap partition within that.   Is this necessary, as well?   If so, how can I do this in the installer's partitioner?   I didn't see the option, only in GParted.

---

### Post by gauravp55 on 2007-06-20
> **Scooter7 said:**
> Okay, thank you, gauravp55 - just one more question, is a /home partition necessary for the install?   And I imagine I set '/home' as the mount point?   What is 'home' for, exactly?   Sorry for all these questions. :p

And, I've seen other Linux partition jobs before - not done them, mind you - and I noticed that they usually have a extended partition, then the swap partition within that.   Is this necessary, as well?   If so, how can I do this in the installer's partitioner?   I didn't see the option, only in GParted.

/home is a directory containing directories of all other users on the system. So if there are 3 user accounts for example then the /home directory would contain 3 subdirectories : one for each user. It isn't necessary for an install.

AFAIK the mount point for the root partition(ext3) is always / as your kernel is located in this partition.

Since you would be dual booting with windows, the Windows partition would be the primary partition of your HD.Remember that a MBR (Master Boot Record) HD can support 4 primary partitions or 3 primary partitions + 1 extended partition. But a given extended partition can contain as many logical partitions as possible. So you never format an Extended Partition by assigning a File System to it..

 Swap is a logical partition and hence it's within the extended partition. In fact when u run Gparted you'll see all your linux partitions as an Extended partition provided you already have Windows installed which should be the PRIMARY PARTITION .

---

### Post by Scooter7 on 2007-06-20
> AFAIK the mount point for the root partition(ext3) is always / as your kernel is located in this partition.

I meant, do I set the mount point for 'home' to '/home'.

Anyway, thanks again to all who replied.   I'll try partitioning... *crosses fingers and hopes he won't screw it up*

---

### Post by Scooter7 on 2007-06-20
Okay, I've set up the partitions, but I want to make sure I've done things correctly - here's a screenshot.   'sdb' is the drive I'm installing to.

I don't get why there's still free space left, though - I told the fat32 partition to use up the remaining space...

[IMG]http://shadowserve.ath.cx/stuff/partitions.png[/IMG]

---

### Post by Scooter7 on 2007-06-20
*bump*

---

### Post by gauravp55 on 2007-06-20
> **Scooter7 said:**
> Okay, I've set up the partitions, but I want to make sure I've done things correctly - here's a screenshot.   'sdb' is the drive I'm installing to.

I don't get why there's still free space left, though - I told the fat32 partition to use up the remaining space...

[IMG]http://shadowserve.ath.cx/stuff/partitions.png[/IMG]

Okay you can extend /dev/sdb3 using Gparted to include the last contiguous free space (429499 MB).. But if you're not too comfortable with doing that, you can create the new partition from Windows.

---

### Post by Scooter7 on 2007-06-20
Okay, I'll try your suggestions. :)

Thanks again,

---

