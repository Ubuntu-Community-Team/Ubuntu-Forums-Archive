---
title: "Win 7 Boot Problem on Dual Boot (Because Partition Was Not Deleted?)"
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by partitionperson on 2012-06-19
Hi,  Im trying to install BackTrack 5 R2 (32bit, KDE) alongside Win 7 (dual boot, from internal HD).  I successfully installed BackTrack, but my problem is that I cant boot Win 7 anymore.  It boots for a while (showing the win logo animation, then going to a bluescreen.) I get this error message on the blue screen when trying to boot Win7: "The Boot Selection failed because a required device is inaccessible." (Status: 0xc0000225)  I think I have realized what is wrong. When running the BackTrack installation I deleted a partition I had recently created in Win 7 (F: with ca 60GB) and created two new ones, a swap of 3 GB and my Linux partition (ca 79GB).  It seems like the old F: partition was not deleted, and I suspect I can correct the problem by deleting it.  But I don't want to mess things up so I thought I'd ask here for advice first.  When running fdisk -l  I get this output:  Disk /dev/sda: 320.1 GB, 320072933376 bytes 255 heads, 63 sectors/track, 38913 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical): 512 bytes / 4096 bytes I/O size (minimum/optimal): 4096 bytes / 4096 bytes Disk identifier: ...     Device Boot      Start         End      Blocks   Id  System /dev/sda1               1           1         992+  42  SFS Partition 1 does not end on cylinder boundary. Partition 1 does not start on physical sector boundary. /dev/sda2   *           1          26      203776   42  SFS Partition 2 does not end on cylinder boundary. /dev/sda3              26       28824   231320576   42  SFS /dev/sda4           28824       38914    81043457    5  Extended Partition 4 does not start on physical sector boundary. /dev/sda5           28824       29189     2928640   82  Linux swap / Solaris /dev/sda6           29189       38914    78113792   83  Linux   Looking at this it seems like my F: is still there, the /dev/sda4 of ca 80GB. sda5 and 6 are using the same cylinders it seems like.  And it seems like the boundaries of sda1 and sda2 are also a potential problem.  When I bought the (HP) lap top it had my C: and two or three other partitions (I saw at least two in windows, but can't remember exactly, and then when managing the partitions in Linux I saw 3 in addition to my C:). (One partition is the backup, and one seems to be only 1 MB large).  Another slightly weird thing is that the F: I created was 60GB but in Linux it seems to be 80GB.  Ok, so my question is: How do I get my Win 7 to work again?  Should I just delete /dev/sda4 ? (Do I need to rename sda5 and 6?) (a strange thing is, I should have to use my old F: to boot Win 7)  Do I have to do anything about the boundaries of sda1 and sda2? I guess they were made like this by HP.   I followed the installation instructions as far as I could, except I had to make the partitions. I also mounted C: as /windows (and I can access it from Ubuntu). MY Linux partition is ext3, if I remember correctly.  When searching for the error code I see suggestions of enabling the APIC, but after checking my partitions, that doesn't seem to be the problem.  Thanks in advance for any advice!  Hopefully asking here can help me save days tearing my hair trying to fix problems :)

---

### Post by ubudog on 2012-06-19
Hi, please do not double post.  I have closed this thread, and I see you have added more information on your most recent post, so please use that thread: 
[http://ubuntuforums.org/showthread.php?t=2006563](http://ubuntuforums.org/showthread.php?t=2006563)

Thanks!

---

