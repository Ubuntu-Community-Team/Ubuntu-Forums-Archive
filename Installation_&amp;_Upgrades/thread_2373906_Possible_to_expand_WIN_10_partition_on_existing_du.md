---
title: "Possible to expand WIN 10 partition on existing dual boot?"
date: 2017-10-10
forum: Installation &amp; Upgrades
---

### Post by flyingsolo on 2017-10-10
I use Ubuntu primarily (16.04) on a desktop with 2 TB disc but must use WIN 10 for work. When I set it up, I was too stingy with the Windows partition which is only 73.2 GB and now 70.45 GB used, and it's crying for more space for updates etc.
Can I safely manipulate the partitions to give more room for windows at expense of my Ubuntu partitions (separate home and partitions for previous U 14.04 and now U 16.04). The following is from fdisk -l.
sda5 is my old U 14.04, not being used any longer; Although sda3 is listed after sda2, on gparted it appears as the last partition(furthest right) which I assume means not physically next to sda2.

```
Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1             2048   29747199   29745152  14.2G 1b Hidden W95 FAT32
/dev/sda2  *      29747200  183333779  153586580  73.2G  7 HPFS/NTFS/exFAT
/dev/sda3       3378276720 3907024064  528747345 252.1G  7 HPFS/NTFS/exFAT
/dev/sda4        183334910 3359031295 3175696386   1.5T  5 Extended
/dev/sda5        183334912  280989695   97654784  46.6G 83 Linux
/dev/sda6        281233408 3236163583 2954930176   1.4T 83 Linux
/dev/sda7       3236165632 3353163775  116998144  55.8G 83 Linux
/dev/sda8       3353354240 3359031295    5677056   2.7G 82 Linux swap / Solaris

Partition 4 does not start on physical sector boundary.
Partition table entries are not in disk order.
```

I'm looking for advice on if I can expand the existing WIN10 partition (sda2) without endangering my Ubutntu install.
Thank you,

---

### Post by yancek on 2017-10-10
One possible, simple solution would be to simply format sda5 to an ntfs filesystem for windows and use it for data.

If you look at the partitions in GParted and sda3 is not shown next to sda4/5 you may be able to do it.  The problem is that you want to extend sda2 (which is a primary partition) to use sda5 (which is a logical partition) and that won't work.

You could use GParted and unmount the logical partitions starting with the highest number then the Extended but before you can extend sda2 to include what is now sda5, you would need to delete sda5 and move the Extended partition to the right to only include sda6, 7 and 8.  Note that if you delete sda5 which is a logical partition, that will change the number of sda6-8, reducing each by one.  This could be a problem booting and your fstab might need to be modified.  You won't be able to do this from your installed Ubuntu but will need a DVD or flash drive.  You will also need to unmount all these partitions before resiizing.

If formatting sda5 to ntfs would work, that would be the simplest and least dangerous since you are no longer using it in Ubuntu.   

Unusual to have an MBR partition scheme with windows 10?  You can thus only have 4 primary partitions which is a big part of the problem you have.

---

### Post by RobGoss on 2017-10-10
You should be able to just **delete** that Linux partition **sda5** and just extend your Windows partition to reclaim that space,
See this YouTube video it's pretty much the same things with Linux partitions [https://www.youtube.com/watch?v=tJiakVgAtn4](https://www.youtube.com/watch?v=tJiakVgAtn4)

---

### Post by Bucky Ball on 2017-10-10
Important: Do NOT use Linux tools to expand or resize a Windows operating system partition (like Gparted or doing it from a 'live' Ubuntu session). Use Windows tools. Windows Disk Management lets you resize Windows partitions. (Vice versa for Ubuntu OS partitions: use Linux tools for resizing, not Win.)

Also, backup anything you don't want to lose prior to doing anything like this. There is always a chance things may take an unexpected turn for the worse.

Good luck.

(PS: Deleting sda5 achieves nothing. That is inside an extended partition. Your Win partition is not. Never the twain shall meet. You also have these errors ...

```
Partition 4 does not start on physical sector boundary.
Partition table entries are not in disk order.
```

... which should be fixed before you go any further (and cause more damage).)

* Just a tip for future reference; the easiest is to make one 40-50Gb Win partition, one 25Gb partition for Ubuntu and use the rest of the drive as a large, NTFS data partition which both OSs can read. You then link the folders from each OS to the folders in the data partition and both OSs access the same data in the same folders. No redundancy, no confusion.

The way you have it, I'd just about bet a house you have copies of the same file residing on the Win OS and Ubuntu OS partitions. ;)

---

### Post by oldfred on 2017-10-10
Use gparted to delete sda5 and move start of extended partition right. That in effect moves unallocated from inside extended partition to next to your sda2 partition.

Then you can use Windows to resize the NTFS partition & immediately reboot and run chkdsk as that is also required after any resize of NTFS.

Ignore error on sda4 extended partition not starting on boundary. You do not write directly into an extended partition, it just acts as a container for all logical partitions. 
But all primary & logical partitions do have to start on sector boundries if a newer SSD or 4K drive (Which your probably is, but you did not post that part of fdisk).

Part of advantage of gpt & UEFI is no primary & logical partitions.
But Windows only boots with UEFI from gpt partitioned drives, so once you have BIOS/MBR very difficult to change.

---

### Post by flyingsolo on 2017-10-11
> **RobGoss said:**
> You should be able to just **delete** that Linux partition **sda5** and just extend your Windows partition to reclaim that space,
See this YouTube video it's pretty much the same things with Linux partitions [https://www.youtube.com/watch?v=tJiakVgAtn4](https://www.youtube.com/watch?v=tJiakVgAtn4)

I've been following this and almost had success. However, after creating Free space where the old U 14.04 was, I can't delete the partition b/c I get an error, "There is not enough space available on the disk(s) to complete this operation." (following the resizing advice in the video link you posted)
Is it referring to my Win 10 space not being big enough (since I am doing this within Win 10 Disk Management)? 
Is there a work around or how much space must be freed up from Win 10 to be successful?
Thanks.

---

### Post by flyingsolo on 2017-10-11
> **Bucky Ball said:**
> * Just a tip for future reference; the easiest is to make one 40-50Gb Win partition, one 25Gb partition for Ubuntu and use the rest of the drive as a large, NTFS data partition which both OSs can read. You then link the folders from each OS to the folders in the data partition and both OSs access the same data in the same folders. No redundancy, no confusion.

The way you have it, I'd just about bet a house you have copies of the same file residing on the Win OS and Ubuntu OS partitions. ;)

Wise advice, I'm sure, but this computer arrangement was established ~2012 with advice from these forums at that time that may not have been 'best in class'! However, my Win 10 use is quite different (ie: work related almost entirely) from U 16.10 so I don't think file redundancy is too bad. Hopefully, in the near future I can update my computer and will follow your advice.

---

### Post by Bucky Ball on 2017-10-11
Did you read the rest of my post? Do not resize Windows OS partitions with Linux tools and *_do not resize Linux partitions using Windows tools_*. Win possibly doesn't know what it is trying to delete. Does it just show the Linux partition as 'Healthy'?

Boot from 'live' media (your Ubuntu install disk/USB), 'Try Ubuntu', launch Gparted when at a desktop, delete the Linux partition.

---

### Post by flyingsolo on 2017-10-11
I hadn't seen your post prior to proceeding with some changes but I have deleted the U14.04 to create unallocated space. However, I can't resize the extended partition (by which, I assume you meant the 1.38 GB partition) b/c there is no preceding or following free space (so it says).
Currently, this is fdisk result. Partitions 2 &3 are separated by the unallocated space I'm trying to access and blend into Win10.

```
Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1             2048   29747199   29745152  14.2G 1b Hidden W95 FAT32
/dev/sda2  *      29747200  183333779  153586580  73.2G  7 HPFS/NTFS/exFAT
/dev/sda3        183334910 3359031295 3175696386   1.5T  5 Extended
/dev/sda4       3378276720 3907024064  528747345 252.1G  7 HPFS/NTFS/exFAT
/dev/sda5        281233408 3236163583 2954930176   1.4T 83 Linux
/dev/sda6       3236165632 3353163775  116998144  55.8G 83 Linux
/dev/sda7       3353354240 3359031295    5677056   2.7G 82 Linux swap / Solaris

Partition 3 does not start on physical sector boundary.
Partition table entries are not in disk order.
```

And, BTW, this is a 2012 computer, so just a big standard hard drive; there is no SSD or modern stuff!

---

### Post by oldfred on 2017-10-11
It looks like your unallocated is still inside the extended partition.
You need to move start of extended right to in effect move unallocated out of extended.
Use gparted.
Only use Windows to expand the NTFS partition after gparted shows the unallocated outside the extended. The extended should have a border around it, it acts like a container for all the logical partitions.

And backup partition table. Windows updates often do not write logical Linux partitions back into partition table. You then have to use testdisk or parted rescue to restore partition(s). With back up you can immediately restore them.

       Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---

### Post by flyingsolo on 2017-10-11
It didn't seem to allow me to move the border of the extended partition but is that just b/c I'm using the system currently. ie: I should perform the change from my bootable linux USB via gparted instead?

---

### Post by RobGoss on 2017-10-11
> **flyingsolo said:**
> I've been following this and almost had success. However, after creating Free space where the old U 14.04 was, I can't delete the partition b/c I get an error, "There is not enough space available on the disk(s) to complete this operation." (following the resizing advice in the video link you posted)
Is it referring to my Win 10 space not being big enough (since I am doing this within Win 10 Disk Management)? 
Is there a work around or how much space must be freed up from Win 10 to be successful?
Thanks.

I've never encountered that when I used Windows disk management, is there an **old Windows, 86** folder that you have after you upgraded to Windows 10? Im just assuming you upgraded, Most people don't deleted this folder and just sits on your machine taking up valuable the disk space

---

### Post by oldfred on 2017-10-11
You cannot edit extended partition while any logical partition is mounted. So no you cannot use gparted on the drive you boot from. 

Use live installer. You may have to also unmount swap with swapoff as live installer usually mounts it automatically.

---

### Post by flyingsolo on 2017-10-12
Success! :D

Thanks mainly to Oldfred's last two posts. (especially the note about Swapoff; that had me stumped for a bit.)
But, as usual, thanks also to everyone's input--I find these the most useful forums on-line b/c I actually get things done and problems solved, despite my own deficiencies! I think I should be good for a while now as Win10 has much more room.
Below is my new arrangement:

```
Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1             2048   29747199   29745152  14.2G 1b Hidden W95 FAT32
/dev/sda2  *      29747200  281228179  251480980 119.9G  7 HPFS/NTFS/exFAT
/dev/sda3        281231360 3359033343 3077801984   1.4T  5 Extended
/dev/sda4       3378276720 3907024064  528747345 252.1G  7 HPFS/NTFS/exFAT
/dev/sda5        281233408 3236163583 2954930176   1.4T 83 Linux
/dev/sda6       3236165632 3353163775  116998144  55.8G 83 Linux
/dev/sda7       3353354240 3359031295    5677056   2.7G 82 Linux swap / Solaris


```

---

