---
title: "[SOLVED] Installing Ubuntu on a hardisk with 2 partitions"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by elnamo on 2008-01-14
Hi,

Please someone explain to me what should I do.

I have one harddisk in the PC with two partition. 

Partition 1 (60GB) is where I install Windows XP- NTFS 
Partition 2 (100GB) is where I store my data - NTFS

I want to discard windows altogether and replace the whole Partion 1 with Ubuntu
My question

1 Can I install Ubuntu on Partition1 without touching Partition2?
2 Can Ubuntu access Partition2 without having to format the partition?

Thank you for yr answers

---

### Post by forestpixie on 2008-01-14
yes 
yes

when you install - direct the partitioner towards the correct partition - choose manual

ubunut reads/writes to ntfs without adding any softyware now

---

### Post by elnamo on 2008-01-14
thanks forestpixie,

that was quick. i'm off to rid myself of this spyware and keylogger laden OS.

---

### Post by abocer on 2008-01-17
I'm facing the same problem now

and I'm talking from the booting CD

can some one help me with the installation plz

---

### Post by forestpixie on 2008-01-17
what do you actually want to know - do you want to do the same as original poster? ie lose windows?

if that's not the case - we need more information from you
if you open a terminal - it's in accessories - then paste this in

```
sudo fdisk -l
```

that should tell us what hard drives and partitions you have

also if you've got to the partitioning stage - do a scrnshot - it's in accessories as well

Edit - accessories are in applications :)

---

### Post by abocer on 2008-01-17
> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa453dbbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2422    19454683+   7  HPFS/NTFS
/dev/sda2            2423       24321   175903717+   7  HPFS/NTFS


what I need to do is to format the partition C to get rid of Windows and install frish ubuntu
without touching the other partition coz three years of my life is in this partition

I hope that explain it

---

### Post by forestpixie on 2008-01-17
OK well we wouldn't wan tyou to lose 3 years of your life - first things first, as you are going to be working on partitions you need to make sure you have backups - you never know whta's going to happen.

When you get to the partitoning stage, go manual and choose the partition that corresponds to the win installation - it SHOULD be sda1, which would have been C:\ , it'll certainly be the smaller of the two - have a look at this page it should help you 
[http://www.psychocats.net/ubuntu/installing#partitioning](http://www.psychocats.net/ubuntu/installing#partitioning)


If when you get to the partitioning stage - you're not sure post a scrnshot of it here

---

