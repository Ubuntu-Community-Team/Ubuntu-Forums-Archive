---
title: "I have a nasty habit of breaking my Ubuntu installs..."
date: 2012-01-28
forum: Installation &amp; Upgrades
---

### Post by krtzer on 2012-01-28
As a result, Ive had to reinstall ubuntu a number of times. I currently have 2 ntfs partitions (one is a bootable windows the other is a system restore), a swap partition, one ext4 partition (that has the broken ubuntu install) and i have another ntfs partition, that I have no idea what it is for. 

I was wondering if could help/tell/point me to a guide to explain how 

1) To remove my broken ubuntu 11.10 install, 
2) Remove the necessary partitions (I'd imagine it would just be the ext4 partition)
3) Make a new small partition to run ubuntu on
4) And with the remaining space, create another file system that I can save my files to.

The idea is that if the ubuntu install breaks again, I can just install over it and not harm any of my files.  

Thanks ahead of time.

---

### Post by jerrrys on 2012-01-28
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=separate+home&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=separate+home&sa=Search&cof=FORID:9)

[https://www.google.com/search?client=ubuntu&channel=fs&q=gparted&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=gparted&ie=utf-8&oe=utf-8)

[http://www.dedoimedo.com/computers/gparted.html#mozTocId801746](http://www.dedoimedo.com/computers/gparted.html#mozTocId801746)

[http://www.dedoimedo.com/computers/gparted.html#mozTocId309606](http://www.dedoimedo.com/computers/gparted.html#mozTocId309606)

another possibility

[http://clonezilla.org/](http://clonezilla.org/)

and welcome to the forums

Edit:  You have gparted if you have the Ubuntu Live CD.

---

### Post by sudodus on 2012-01-28
> **krtzer said:**
> As a result, Ive had to reinstall ubuntu a number of times. I currently have 2 ntfs partitions (one is a bootable windows the other is a system restore), a swap partition, one ext4 partition (that has the broken ubuntu install) and i have another ntfs partition, that I have no idea what it is for. 

I was wondering if could help/tell/point me to a guide to explain how 

1) To remove my broken ubuntu 11.10 install, 
2) Remove the necessary partitions (I'd imagine it would just be the ext4 partition)
3) Make a new small partition to run ubuntu on
4) And with the remaining space, create another file system that I can save my files to.

The idea is that if the ubuntu install breaks again, I can just install over it and not harm any of my files.  

Thanks ahead of time.
Welcome to the Ubuntu Forums :-)

0. Backup your data (either everything or your personal data) regularly to a separate hard disk drive, for example a USB or eSATA drive. This is really important, and will save you a lot of worries and trouble in the future. It is particularly important before editing the partitions, because it is risky!

0.5 If you want to keep Windows, defragment its file system.

1. Edit your hard disk drive with Gparted from a live CD or USB drive. This means that you boot from an external drive, for example your Ubuntu install drive (which contains Gparted (among the System Administration tools). You should always boot from another drive, and leave the partitions on the drive-to-edit **un**mounted.

2. Decide which partitions to keep! I suggest that you keep Windows for a year, until you know that you won't need it. And keep a data partition with NTFS file system, that is réadable and writable from both Windows and Linux.

3. Tell us how much space you have: post the output of
```
sudo fdisk -lu
```
mount all partitions and post the output of
```
df
``` Cut and paste and put code tags around the output text with the # icon at the top of the editing window!

4. Finally consider a /home partition and a swap partition.

*. Probably you will keep two partitions. I suggest that you shrink them to leave space for Ubuntu. Then make an extended partition or two, if it cannot be contiguous. And make logical partitions inside the extended partitions. Anyway, you can have only four primary + extended partitions, but many logical partitions.

---

### Post by BC59 on 2012-01-28
Should be a good idea to post a screenshot of the Gparted picture.

---

### Post by krtzer on 2012-01-28
Here is the image from df :
[IMG]http://imgur.com/I8dJP[/IMG]
The picture doesn't seem to be uploading so I uploaded it to imgur:

[http://imgur.com/I8dJP](http://imgur.com/I8dJP)

---

### Post by sudodus on 2012-01-29
Well, according to ***fdisk*** the partition types and sizes look good to me :-)

But you did not mount these partitions, so they are not included in the output of ***df***. Please do that: mount the partitions and then run ***df*** again, or do what BC59 suggested: post a screenshot of gparted, when it looks at /dev/sda, because it would show the same information (how full are the partitions?)

---

### Post by krtzer on 2012-01-29
Ok, so I have a new problem now, well one that I think could be fairly solvable.

Tutorial used:

[http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html](http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html)

First I installed the latest version of 11.10 to the drive /dev/sda6. That went fine.I was able to log in and make sure everything was updated. Then I used Gparted, as the tutorial said, and shrunk that file system and made /dev/sda7 from the unallocated space.  Still, no problems logigng back on. I logged back onto 11.10 on the hard disk and configured the newly made partition, and followed step 3 part E) and F) of that tutorial. I rebooted the computer and couldn't login to as the main user. I also noticed that the menus looked weird, which made me think that not all the files were in the right place. So I booted back into my ubuntu live cd, and took a looks at the 2 drives in question. There was only 1 folder in /dev/sda7/ (lost and found). 

I am not sure how to mount the drives and take a look at their contents in terminal, but I have screenshots of gparted, and the contents of the two drives in question and the current GParted shot:

[http://imgur.com/UHW4p,MRvla,RYmA8#0](http://imgur.com/UHW4p,MRvla,RYmA8#0)

---

### Post by darkod on 2012-01-29
Can I suggest a much easier approach?

Since you are already making a new install it makes no sense installing without a separate /home partition and then immediately trying to create one.

Start the install again. Select the manual partitioning option (Something Else). Once the list of partitions on the disk shows up, do:
1. Delete both sda7 and sda6. I am guessing from what you said earlier, you still have sda5 as your swap partition.
2. Create a new sda6 partition with size 15GB, type ext4, mount point /.
3. Create a new sda7 partition from the remaining unallocated space, type ext4, mount point /home.

Problem solved. In future, when making new clean installs, use sda6 with mount point / and tick the format box. Use sda7 with mount point /home but DO NOT tick the format box. That keeps the data on /home untouched.

---

### Post by krtzer on 2012-01-29
^ This. Everything is working now, thank you. There were a few errors while installing, i tried to make error reports but they didn't seem to go through. There were errors installing, one while it was installing flash, and the other one I saw was in updating the certs. They still look like they're there though, so I'm not sure what the issue was. 

Now off to try to install openCV again. Thanks to everyone who posted.

---

