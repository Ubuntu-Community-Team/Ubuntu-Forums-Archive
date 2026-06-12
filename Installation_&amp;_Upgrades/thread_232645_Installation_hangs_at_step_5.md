---
title: "Installation hangs at step 5"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by br77 on 2006-08-09
I've been trying to install Dapper Drake (Japanese version) from a downloaded ISO image burned to CD-ROM on a new laptop that came without an operating system. As soon as I came to step 5, choose one of the options (any option except the manual partition table option), and click next, the CD-ROM drive chuggs away and the hard disk light flashes but never progresses. I've waited as long as 2 hours and seen no progress to step 6.

I check the partitions on the drive with fdisk, saw that there was a small FAT32 partition and removed it. I then added my own /, /home, and swap partitions (once with gparted and once with the installation manual partition option), and it still refuses to progress to step 6.

Here's where things get strange, though: I removed all of those partitions with fdisk (leaving the HD with no partitions), started up the installation program, chose the "use largest free space" option, and it progressed to step 6. At this point, I stupidly returned to the previous step and entered the manual partition choice thinking that I'd really like to have a /home partition. The computer then wouldn't progress to step 6.

I've tried recreating the conditions of that one successful trip to step 6, but nothing works. No matter what, it won't progress beyond step 5. Am I missing something? Did I inadvertantly do something vital with that first partition deletion? Do I need to be manually mounting /dev/hda or something?

If possible, I really would like to set up the partition table myself, although I guess I can live without a /home partition.

---

### Post by 5-HT on 2006-08-09
What about trying the Alternate install CD instead?
I was having partitioning issues with the Live/Desktop CD, and ended up doing the install using the Alternate CD without any problems.

---

### Post by br77 on 2006-08-09
> **5-HT said:**
> What about trying the Alternate install CD instead?
I was having partitioning issues with the Live/Desktop CD, and ended up doing the install using the Alternate CD without any problems.

Is there an Alternate install CD for the Japanese version? I couldn't find it on the Japanese Ubuntu site where I downloaded the ISO image that I have now.

---

### Post by br77 on 2006-08-12
Ok, I figured out that I just had a bad disk. I downloaded the ISO again, burned it (slowly at 4x), and was able to fly through the installation. No issues whatsoever, and I have to say, one of the easiest Linux installs I've ever experienced... then again, my last install was back in 1998.

Anyway, for any installation hang issues, you might just have a bad disk. Burn a new one.

Brian

---

