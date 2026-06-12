---
title: "NOOB HELP - Manual Partition and Format Question"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by BradGavVenice on 2008-04-29
My two questions are listed in **Bold** below. I have also included all the other relevant info I could think of below.

Ubuntu Day 2...
Yep, I'm two days into learning about UNIX/Ubuntu from scratch. I just discovered Ubuntu last week and I am very interested in using it. To date I have followed the instructions I could find in these forums to the letter and so far the process has been successful. During the 8.04 install I arrive at the 'Prepare Partitions' step and I'm not sure how to proceed. Here are the steps I have taken to date:

[INDENT][LIST=1]
[*]Successfully downloaded and installed the rEFIt Boot Menu.
[*]Downloaded Ubuntu 8.04 LTS Desktop Edition for Standard PC (32bit). I successfully verified both the download and the CD after burning.
[*]I have been following the 'Ubuntu Installation (Triple Boot)' instructions at: [https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)
[/LIST][/INDENT]

These installation steps were originally written for 7.10 (Gutsy Gibbon) and the 8.04 'Manual Partitioning' steps seem to be a bit different. I'm not sure how to proceed on the 'Edit a Partition' screen:
On the 'Prepare Partitions' screen I select '/dev/sda3 fat32' as instructed, which is 34027 MB in size.
This leads to 'Edit a Partition' - New partition size will be 14000 MB, approximately half the size of this partition.
'Use As' comes up as 'do not use the partition' by default. With this setting it does not allow me to set the 'Mount Point' to '/media/Windows'...
[B]Which 'Use As' format should I select? (The choices are: Ext3, Ext2, ReiserFS, JFS, XFS, FAT16, FAT32, swap area, EFI Boot Partition, or do not use the partition") From the instructions it appears that I should be trying to make free space. 
Lastly, in the 'Edit the Partition" screen should I check the 'Format the Partition' checkbox, or leave it blank?[/B]

Here is the current setup of the Volume before :
[INDENT]'/dev/sda'
free space (0 MB)
/dev/sda1 efi (209 MB) Used 209 MB
/dev/sda2 hfs+ (215687 MB) Used 125800 MB
free space (134 MB) zero Used
/dev/sda3 fat32 (34027 MB) Used 3900 MB
free space (0 MB)[/INDENT]

Here are the specs of my computer:
[INDENT]MacBook Pro 15" (1,1)
Processor: 2 GHz Intel Core Duo
Memory: 2 GB 667 MHz DDR2 SDRAM
Mac OS X 10.5.2[/INDENT]

Any help would be greatly appreciated. These forums have been invaluable and I hope to be a helpful contributor some day! Thank you

---

### Post by zvacet on 2008-04-30
Back up your fat32 partition (data on it) and then delete it.On that free space you will install Ubuntu on ext3 format.

---

### Post by BradGavVenice on 2008-04-30
Thank you for your suggestion but I'm not sure I understand your logic. If I delete the fat32 partition and format as ext3 - how do I get the Windows partition back? The Triple Boot instructions seem to indicate there is a way to split the fat32 partition and use half for Ubuntu. I can reinstall Windows no problem but I don't want to lose the fat32 partition completely because I use a few windows apps for work. Any further thoughts would be greatly appreciated. Thank you.

---

