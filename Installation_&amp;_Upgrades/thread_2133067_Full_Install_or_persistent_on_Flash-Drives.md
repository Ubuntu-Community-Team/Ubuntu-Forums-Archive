---
title: "Full Install or persistent on Flash-Drives"
date: 2013-04-06
forum: Installation &amp; Upgrades
---

### Post by Aiken Pandora on 2013-04-06
hello, is it so much better to install just a persistent Live Ubuntu on a flash Drive then an full Install of Ubuntu? Is a full install so dangerouis for a USB-Flash-Drive? Cause of the limited write cycles?  sorry for my bad english, but i hope you can give me some advices.

---

### Post by ahallubuntu on 2013-04-06
~

---

### Post by fantab on 2013-04-06
> **Aiken Pandora said:**
> hello, is it so much better to install just a persistent Live Ubuntu on a flash Drive then an full Install of Ubuntu? Is a full install so dangerouis for a USB-Flash-Drive? Cause of the limited write cycles?  sorry for my bad english, but i hope you can give me some advices.

One major difference will be that 'full install' on HDD will be lot faster than on the Persistant Flash Drive. A Full install on Flash Drive too will be faster than Persistant but not as fast as when installed to a HDD.

Persistant is good if you want to "Try Ubuntu" for a while, make changes to it, install and check applications and configurations etc before you actually do a full install. If you have good 3.0 USB Flash Drive with more than 8GB space then you can consider full Ubuntu install on it if you want to carry around your Ubuntu.

---

### Post by C.S.Cameron on 2013-04-07
Last weekend I did a variety of installs to flash drive and ran some simple benchmarks.

Installs included:
Full install, no swap.
Full install, swap.
Full install, separate ext2 home partition.
Full install, swap + separate ext2 home partition.
Full install, swap + separate ext2 home partition + FAT32 partition.
Persistent, casper-rw file.
Persistent, casper-rw partition.
Persistent, casper-rw + home-rw partition.
Persistent, casper-rw + home-rw partitions with Try/Install screen removed.
Grub2 Iso boot, Persistent, casper-rw + home-rw files.

I tried again after removing journaling and adding noatime on the Full installs.

Benchmarks included Hardinfo and Bootchart.

Bootchart, Full install vs Persistent, 22 seconds vs 145 seconds, persistent install with try/install removed, 114seconds.
Hardinfo, All install types had similar scores.
All shutdown times similar.
**I did not notice a difference in speed in the little time I played with each**.

As for flash drive life, most decent drives have wear leveling. If you do the math based on 10000 writes, you will find that a flash drive should last several years being used full time forty hours per week.

One big benefit of a Full install is security.
The persistent casper-rw file is easy to mount and extract data from.

Another advantage of Full install is the ability to update and upgrade. 

One advantage of a Persistent install is that it uses less space and can be installed on a 4GB drive.

---

### Post by Aiken Pandora on 2013-04-07
thanks for your replies,
to be honest, I wanted to chose the full install, because i didn´t liked the persistent try version (got it on a 4GB Stick).

So choosing ext2 will deactivate journaling? (just ext2 for the home partition or for all?) Is there another way, to deactivate the journaling function or is this function implemented in the EXT 3 and 4 Data System?

Sorry, but what is noatime?

Yeah, i bought a new 64 GB SanDisk USB-Flash Drive, this one is even quicker then my HDD, but i never needed a quick HDD, just wanted to play games on my Windows PC and its loading quick enough.

Swap Partition is just necessary for the hibernation or is this important for sth. else?

thx for your advices and sorry if one of this Question is answered in another thread, didn´t find anything in the search, but i am not that good in english.

Again thank you.

---

### Post by oldfred on 2013-04-07
From 
man mount
>        noatime
              Do not update inode access times on this filesystem  (e.g.,  for
              faster access on the news spool to speed up news servers).

Which means everytime you read a file, it will not write that back into the inode as last accessed. Reduced writes improve speed on flash drives or SSDs.

I use ext4, but turn journal off. Supposedly ext4 has some other advantages, but I do not know details.

Trim is only available for SSD, otherwise settings  are similar.
 With SSD or Flash drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
Make sure BIOS is in AHCI mode for trim to work.
change to noop i/o scheduler

I changed to noop, but now deadline may be better?

 [http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_iosched_2012&num=1)

---

### Post by C.S.Cameron on 2013-04-07
What seems to be working for me with a 16GB flash drive is half NTFS and half ext4 with no swap.
Journaling has been turned off, so a separate ext2 home partition is probably not necessary. 
Noatime has been added to fstab, (I'm not sure about this one yet)

---

### Post by Aiken Pandora on 2013-04-07
sounds good, i think i will change the fstab, i don´t need to know, which time i accessed a data recently and with less writing on the USB-Stick he may hold some hours longer :)
I think the Drive will be quick enough, i read some test about the device which says its got 190 MB/s read and 170 MB/s write and thats much better then my HDD with 30MB/s.

Thank you for the help, i will write when i installed the system to my usb-drive. As soon as i get the device from the local postman.
As next i will set up a PC as a Linux-Server.

---

### Post by Aiken Pandora on 2013-04-10
tourning off the journaling function is just to boost the speed or also to save the usb flash-drive?
and can i somehow see if it worked and journaling is off for my ext4 Partitions?

---

### Post by oldfred on 2013-04-10
You can use this - long list of parameters I only show some of mine:

Before:
 ```
Filesystem features:      [COLOR=#ff0000]has_journal[/COLOR] ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize

```
    fred@fred-Precise:~$ [COLOR=#ff0000]sudo tune2fs -O ^has_journal /dev/sde2[/COLOR]
tune2fs 1.42 (29-Nov-2011)
After:
```
fred@fred-Precise:~$ [COLOR=#ff0000]sudo tune2fs -l /dev/sde2[/COLOR]
tune2fs 1.42 (29-Nov-2011)
Filesystem volume name:   <none>
Last mounted on:          /media/6d3eae0b-edfb-47a7-94f9-3e0abf6bda23
Filesystem UUID:          6d3eae0b-edfb-47a7-94f9-3e0abf6bda23
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
```

---

