---
title: "Dual Boot with Win98"
date: 2005-06-11
forum: Installation &amp; Upgrades
---

### Post by sandman55 on 2005-06-11
Hi I've been helping my neighbour setting up a new hard drive for Win98 and Ubuntu, its a **40 gig** drive and we have partitioned it with an approx **20 gig** Primary partition (**C:**) which we've installed Win98 then we made an extended partition **(of 20 gig)** on which we made two logical drives** D:** aprox **10 Gig** (for backing up win98 files) and** E:** the remainder (for Ubuntu). 

Tomorrow we intended to put Ubuntu Warty on the** E:** logical drive (I know linux numbers drives differently). Now I've been thinking if I put Ubuntu on the **E:** logical drive will that render the** D:** drive inaccessible to win98 because** D:** and** E:** are on the one extended partition. Should I redo the extended partition with just **10 gig** with one logical drive **D:** and leave the remaining space of approx **10 gig** untouched for ubuntu to be installed on.

Thanks in advance

---

### Post by az on 2005-06-11
The two logical drives are two different partitions.  Windows will still see your E: drive....

It will just be renamed D:, since the current D: will no longer be windows-readable.

---

### Post by sandman55 on 2005-06-11
Thanks azz. 

I thought as I had to put the two logical drives D: & E:  in the one extended partition it wouldnt work, I still have to get my head around this partitioning.

Thanks again we will give it a go tomorrow.

---

### Post by sandman55 on 2005-06-11
[QUOTE=azz]The two logical drives are two different partitions.  Windows will still see your E: drive....

It will just be renamed D:, since the current D: will no longer be windows-readable.[/QUOTE]

Sorry I just reread your post  with my three drives C: D: & E:  with Ubuntu on the E: drive will my D: drive remain fat 32 and will the little bit of data on it remain untouched (it is backed up) and will I still have 3 drives C: D: and Ubuntu where E: was?

thanks in advance

---

### Post by az on 2005-06-11
The installer will not touch a partition unless you tell it to.

---

### Post by sandman55 on 2005-06-12
[QUOTE=azz]The installer will not touch a partition unless you tell it to.[/QUOTE]

Thanks azz  :)

---

### Post by sf-andrew on 2005-06-17
I hope you don't mind me adding my question to this, as it does relate to setting up a dual boot with Win98.

I have a machine running Win98SE, and I have just replaced the hard drive so that I now have 80GB. I have transferrred my Win98SE setup to the new drive. My plan is now to install UbuntuLinux. 

I want to be careful so that I don't delete my Win98SE installation. I therefore created a new partition (of around 40GB), using the tools that came with the Western Digital disk. However, when I then started to install Ubuntu (choosing the option to manually assign partitions, I found that it did not report there being any partition present. I wondered whether it was something to do with the way the partitioning had been done, so I therefore downloaded and burned a CD containing QTParted, and set up some partitions - as shown below, formatting the new ones to be ext3 and with the appropriate names for the Ubuntu installation. 

Incidentally, I also made the new root partition to be active (probably unnecessarily, since I later had to make the Windows partition active again before the computer would boot from it). Also, from reading other postings I realize that the swap directory shouldn't be so large.

Set up using QTparted:
........Partition.....Type....Status....Size......Used Space.....Start......End.........Label
01..../dev/hda1...fat32................37.44GB...17.26GB......0.03MB...37.44GB...DRV2_VOL1
02..../dev/hda2...ext3...Active.....31.25GB.....1.59GB.....37.44GB...68.68GB.../
03..../dev/hda3...ext3....................5.84GB...331.31MB...68.68GB...74.53GB.../swap

I then started up the Ubuntu installation again. Now I was nervous about where Ubuntu would be installed, so I went into the manual partitioning again. Once again, the partitions reported by the installer seem to bear little resemblance to the partitions that I thought I had created.

Reported by Ubuntu:
IDE master (hda)   80GB    WDC WD800...
........#1 primary    8.4GB    <lightning>
..............pril/log     35.8GB   FREESPACE
........#2 primary    35.8GB   ext3
IDE slave (hdb)    20.0 GB  IC35...
........#1 primary   20.0GB   <lightning> FAT32

I therefore aborted the installation and decided to seek help!

What am I doing wrong here? Do I even need to go through the manual partitioning stage now that I have already done my partitioning elsewhere? Is there any danger of me installing Ubuntu in my Windows partition? Where should GRUB go, or should I be using LILO? What is the difference between "primary" and "pri/log", and do I need to know it? 

Presumably the <lightning> symbol refers to the partition being a boot partition. ...yes, the slave drive was my original drive and I have not wiped it yet as it is my backup in case everything goes wrong.

Sorry about all the questions... any advice would be much appreciated.

---

### Post by jerrykenny on 2005-06-17
sf-andrew,

If you're not sure about your disk partitioning, use the ubuntu disk to remove your original LINUX partitions, and then recreate,

1     An extended partition (the full size of the remaining diskspace)

2     Logical drives within the above, . . . . eg

              100 mb        for /boot    use ext2
              500 mb        swap 
              39 Gb          rest of drive in fact, ext3, for  /    


Swap likes to be near the start or middle of the drive for better performance.




Use grub,  lilo might have problems as it will have to be installed miles from the start of the disk.   Probably it would be OK, but on some hardware lilo wont work if its further than 7Gb from the start of the disk.

Good Luck



As an alternative,  remove your new hard drive,  and install linux onto your old 20 Gb drive.    Your new one cant then come to any harm, and you can then later edit the file   /boot/grub/menu.lst   so you can dual boot

---

### Post by sf-andrew on 2005-06-17
Thanks for the reply.

So which of the above lines (reported by Ubuntu) do I modify? I don't want to touch the windows partition, so presumably I shouldn't touch the two lines referring to #1. That therefore leaves the "#2" line reporting 35.8GB.

I am interested by your suggesting a separate /boot which is formatted differently (ext2). I haven't seen that anywhere else. What does that do?

If I do put linux onto the old drive and make it the primary master, then presumably I won't be able to boot into Win98 any more - or will GRUB allow me to direct the computer to boot up from the primary slave drive?

---

