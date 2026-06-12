---
title: "Switching from Vista to Ubuntu"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by punjabdasher on 2008-11-16
So I've decided to make the switch however there is the problem of migrating all my data from Vista over to Ubuntu, what would be the best way to do that (it is over 60 GB of data so burning DVDs isn't exactly an option)?

---

### Post by 505 on 2008-11-16
The best way is to place it on another partition. Do you have enough free space on your hard drive? If so, make another partition (you can do that using the live CD). Then copy all that data to the new partition. Then install Ubuntu on the Vista partition. In Ubuntu, you can then mount the partition you just created.

---

### Post by fballem on 2008-11-16
I have used external USB hard drives with great success. Store the data from Windows and retrieve it into ubuntu. External hard drives prices have come down a lot. In Toronto, we can get a good size external hard drive (160gb) for under $100 at Best Buy. I use an external USB hard drive for my backups.

Depending on the type of data you have, programs in ubuntu may be able to work with it directly. Other data may need to be converted, either in Windows or in Ubuntu. If you use outlook or outlook express for e-mail, you will need to convert these prior to migrating from windows. As well, if you have music in Windows Media Lossless format, these will need to be converted in Windows.

The information that I gained in this this Thread was really helpful when I first switched to ubuntu from Windows: [http://ubuntuforums.org/showthread.php?t=786515&highlight=fballem](http://ubuntuforums.org/showthread.php?t=786515&highlight=fballem) Some of it is specific to ubuntu 8.04, but most of it is still applicable.

Hope this helps,

---

### Post by punjabdasher on 2008-11-16
> **505 said:**
> The best way is to place it on another partition. Do you have enough free space on your hard drive? If so, make another partition (you can do that using the live CD). Then copy all that data to the new partition. Then install Ubuntu on the Vista partition. In Ubuntu, you can then mount the partition you just created.

My only fear is that I have heard that repartitioning your Vista partition would render it unusable, and although I do want to remove Vista completely, I still would need to access Vista in order to copy the files from my Vista partition to the new partition.

---

### Post by fballem on 2008-11-16
> **punjabdasher said:**
> My only fear is that I have heard that repartitioning your Vista partition would render it unusable, and although I do want to remove Vista completely, I still would need to access Vista in order to copy the files from my Vista partition to the new partition.

Not if you were to use an external drive. Copy the files to the external drive, including any conversions for e-mail. Once that's done remove the external drive and set up your machine for ubuntu. You can then copy the files from the external drive into ubuntu.

---

### Post by MatMan on 2009-01-22
does it matter what file format the external hard drive is formatted as? NTFS or fat32 etc?

---

### Post by Mark Phelps on 2009-01-23
It matters only from the standpoint that FAT32 can't hold files larger than a certain size.  I think it's 2GB, but I'm not sure.  I know it can't hold an ISO image of a 4+GB DVD.  Current Ubuntu versions come with the NTFS-3G package that can read and write NTFS partitions.

---

### Post by tom56 on 2009-01-23
> **Mark Phelps said:**
> It matters only from the standpoint that FAT32 can't hold files larger than a certain size.  I think it's 2GB, but I'm not sure.

The limit is 4GB

---

### Post by russu52 on 2009-01-23
get an external HDD - excellent for backups. a 1T HDD is around 130 euro over here. best if formatted ntfs. you will be able to use it on ubuntu or windows

---

### Post by tom56 on 2009-01-24
I agree. I have a 500GB external drive that I got for £50. I use it to make a weekly backup, and it often comes in handy for moving around large files, or if I need to reinstall. I way very thankful for it when my laptop died and had to be sent off to HP. It meant I could keep working by plugging my external drive into my girlfriend's computer.

---

### Post by WatchingThePain on 2009-01-24
I use the wubi and when using Linux it has no probs seeing the widows partition (ntfs) and files. Just go into hosts directory.

---

