---
title: "Partitions not being recognized"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by ricardosilva on 2008-01-04
I am having a problem installing Ubuntu!

I have downloaded the ISO file for the Live Cd and burned the CD. Ubuntu starts fine from the CD boot.

I am now at the point when I want to install Ubuntu, but I am having a problem.

My hard drive has 3 partitions: one for Windows Vista, one for Fedora, and one for HP_RECOVERY.
What I want to do is the following: shrink my Vista and Fedora partitions, create a new Ext3 partition for Ubuntu, create a new Fat-32 partition for data (to be shared by the 3 systems), create a new swap partition and a new partition for /home.

I know this might be complex, especially being the first time I mess with partitions (the partitions I have now were done by the people at the store where I bought my computer, I had asked for Windows and Linux to be both installed). But I thought I had understood what to do.

The problem is that when I try to install Ubuntu, and I choose to do the partitioning manually, it doesn't recognize any partitions, it treats my whole hard drive as a unique chunk, as if I didn't have any partition at all.

What does this mean?

Thank you for your help.

---

### Post by forestpixie on 2008-01-04
I would use the vista tool to shrink it's partition - and would use a gparted livecd, which you can download here [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/) to do the remaining partition work

Be aware that you are you going to have to use extended and logical partitions - do the shrinking - then make an extended in the free space - create you new partitions within that

Once you've done that you can restart the ubuntu livecd and when you get to the partition part - use the manual option

---

### Post by ricardosilva on 2008-01-04
Thank you, forestpixie for your help, but I don't understand everything you say.

I think it might be better to do nothing unless I'm sure.

Here is what I understood I should do:
1  - Go to Administrative Tools->Computer Management and use the options there to shrink the Volume of the partition associated with Windows at the moment
2 - Download and burn a gparted live CD
3 - Use the CD to create all the other partitions
4 - Install Ubuntu from the CD

Now, my questions are the following:
What are logical and extended partitions?
I still have no idea why Ubuntu installer can't recognize the partitions I already have at the moment. I guess the same thing will happen to me after I create the partitions I want in the end.

---

### Post by forestpixie on 2008-01-04
It's always better to be sure :)

Logical and Extended partitions
a hard drive can only have 4 primary partitions - in order to have more than that we use extended partitions - because an extended partition can have more than 4 partitions inside it 

as far as why the installer doesn't see the exisitng partitions, did you check the md5sum for it - or at least verify the disc before you let it boot

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

We can try and have a look at what is going on though - boot the livecd and then open a terminal - that will be in applications >accessories, paste this command in and we should be able to see what partitions you have

```
sudo fdisk -l
```

This page - although a mighty tome has info at the beginning on primary, extended and logical partitions - [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)


Please post back if you need to

---

### Post by ricardosilva on 2008-01-05
OK, running sudo from the fdisk gives me the following:

sda1    NTFS   (Windows Vista)
sda2    Linux   (Fedora)
sda3    NTFS   (HP_Recovery)

I can see from Windows all these partitions are primary.
I am quite a beginner, but I was surprises to see this. Shouldn't there be another extension for Fedora's Swap file?

 I had already checked the CD with md5sum, it was ok. I still have no clue why Ubuntu doesn't recognize the partitions, but I'm glad it didn't, otherwise I would have screwed up on my first attempt.

I can't shrink my Windows partition from within Windows, is it possible to do it from Gparted?
About Gparted, I have downloaded the livecd, I will try it out now.

Thank you once again.

---

### Post by ricardosilva on 2008-01-05
Ok, I am even more confused now...

Gparted does not recognize the partitions.
When I start Gparted from the livecd, it shows me my HD as one big, unallocated chunk.
What do I do now?

---

### Post by forestpixie on 2008-01-05
yea - I can imagine you are - it's confusing me 

vista won't let you shrink it's partition - 1st question is there enough room

yes I would of thought there'd be a swap for fedora as well

could you post a scrnshot of the gparted from ubunut livecd

and perhaps post the whole output for sudo fdisk -l

---

### Post by ricardosilva on 2008-01-05
OK, I'll post a screenshot of Gparted and also the full info from fdisk (I'll take about 5 min).

Just one thing... I did not run Gparted from the Ubuntu liveCD. I downloaded and burned a Gparted live CD and ran it from there.

---

### Post by ricardosilva on 2008-01-05
ubuntu@ubuntu:~$ sudo fdisk -l 
 
Disk /dev/sda: 160.0 GB, 160041885696 bytes 
255 heads, 63 sectors/track, 19457 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x65cc0fcc 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        9744    78268648+   7  HPFS/NTFS 
/dev/sda2            9744       18438    69830656   83  Linux 
/dev/sda3           18438       19457     8188928    7  HPFS/NTFS

---

### Post by ricardosilva on 2008-01-05
I can't take a screenshot of Gparted

---

### Post by ricardosilva on 2008-01-05
I was able to take a screenshot of Gparted:

---

### Post by Pumalite on 2008-01-05
You have solve your problem from WITHIN Vista; otherwise you won't be able to run anything in that computer.

---

