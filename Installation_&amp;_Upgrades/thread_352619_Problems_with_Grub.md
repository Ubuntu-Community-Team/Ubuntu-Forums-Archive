---
title: "Problems with Grub"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by Kiram on 2007-02-03
I've been using Ubuntu for a while now on my main PC, so I decided to try a dual boot on my Laptop. Everything was working fine, but I had some unsolvable errors with Ubuntu. I decided that it was just better to kill the project for a while and try again sometime later. In order to free up the 40 gigs of HD space I had set aside to my Ubuntu installation, I just straight up deleted the partitions and reformatted them as a separate NTFS partition. Apparently, that was not a smart move. 

When I finally got around to doing a full reboot, GRUB wouldn't work. The output looked like this:

GRUB loading, please wait...
Error 17

Now, because I've moved some files onto my second partition, I'd really rather not be forced to reinstall Ubuntu, since I'd have to format that partition and lose all my data. As it is, I cannot currently get into windows at all. Any help here would be greatly appreciated. (It should be noted that my Windows partition is a FAT32 file system.)

---

### Post by housam on 2007-02-03
For windows, I think that you have to fix the MBR to enable booting it again. 
For ubuntu , you have to reinstall it again after reformat its partition to ext3 as ubuntu can't be installed on ntfs format.

---

