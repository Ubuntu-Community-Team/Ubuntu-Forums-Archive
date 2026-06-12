---
title: "Installation hangs at Partitioning stage"
date: 2005-09-08
forum: Installation &amp; Upgrades
---

### Post by chscag on 2005-09-08
Hi:

Trying to install version 5.10 preview.  Install seems to go OK except when it gets to the stage where it wants to partition the disk.  It then displays 5 question marks and will not proceed any further.

I'm attempting to install 5.10 over my current installation of MEPIS which is on a partition formatted to ext3.   The disk really does not need partitioning, I only wish to install 5.10 in place of MEPIS.  Can anyone tell me how to do that without partitioning the disk?  The disk also contains several FAT-32 partitions related to WinXP which I do not wish to erase!   [-X 

Thanks.    :)

---

### Post by Cashel on 2005-09-09
I havent been through the test Ubuntu myself (5.04 is "stable" and you may want to go back to that if you're having problems) ... otherwise I dont see why you are worried about partitioning if all you are worried about is losing windows partitions and not the partition your installing over, there is no reason you should have to reformat an entire drive to change one partition.. simply delete the ext2 and let the partition dialog "use largest free space" if thats an option or create a new drive in the blank space.. as I said tho I havent seen the testing version.... 

maybe one of these ubergeeky guru fellas can be of further help if that doesnt cut it! Good luck!

---

### Post by chscag on 2005-09-09
Thanks for the suggestion.   I removed the MEPIS partition by using Partition Magic from a DOS prompt.   Booted the install CD again - this time it picked up the free space OK and proceeded with the install.   So far so good with the Preview version.
 :)

---

