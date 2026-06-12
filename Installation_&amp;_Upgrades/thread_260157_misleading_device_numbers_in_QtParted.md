---
title: "misleading device numbers in QtParted"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by mkuutti on 2006-09-18
I managed to destroy my windows ntfs partition with qtparted from kubuntu 6.06.1 live/install-cd.
I found soulmate from linuxquestions.org:

[http://www.linuxquestions.org/questions/showthread.php?p=2398269](http://www.linuxquestions.org/questions/showthread.php?p=2398269)

My problem:
I just downloaded kubuntu 6.06.1 i386 image in order to replace my amd64-kubuntu with 32bit version. I have also windows XP x64 and **had** windows XP-32bit version. I had following setup:

300GB sata disk:
/dev/sda1 ntfs 20GB (XP x64 "C:")
/dev/sda2 ext3 30GB (kubuntu amd64 "/")
/dev/sda3 swap 1,5GB
/dev/sda4 extended 
/dev/sda5 ntfs 200GB (win "D:")
/dev/sda6 ntfs 30GB (XP 32 "E:")

My plan was to resize /dev/sda5 -> 170GB and create 30GB ext3 partition for "/home" where I could backup my home-dir from /dev/sda1. Qtparted did the job and new 30GB partition appeared as /dev/sda6 and my "last" ntfs-partition moved to /dev/sda7. It seemed logical but then I right-clicked "Format" to new partition /dev/sda6 and result was that it formatted my 32-bit XP partition (which was originally /dev/sda6). I checked with fdisk that new linux-partition number was /dev/sda7, not /dev/sda6 like qtparted showed. So somehow I can confirm this misleading behaviour.
 
It would have been better for me if it had been that XP x64 partition that destroyed, which is waste of blocks in disk. Well, now I can reinstall partitions however I want...

---

