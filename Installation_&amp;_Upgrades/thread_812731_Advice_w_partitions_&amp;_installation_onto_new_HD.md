---
title: "Advice w/ partitions &amp; installation onto new HD"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by behindtheeye on 2008-05-30
Hi folks,

I've recently acquired a new SATA 500GB hard drive as I'm out of space on my current one (IDE 180gb I think). I'm currently just running Windows XP but now I have the new drive I want to install Ubuntu 8.04 and get a dual-boot going. I do want to keep both drives active.

Can anyone recommend how I should partition / arrange the drives for best results? I'd like a large area to store files (music, videos etc) that I can access from both XP and Ubuntu. I've done a quick format of the new drive from Windows but the drive is currently empty.

No doubt I've missed some details out here, let me know if you need any more info.

Thanks in advance,
Matt

---

### Post by didac on 2008-05-30
When you start Ubuntu installer, it will ask you where to put /. Make it the new hard disk. Your files can go to that hard disk. Ubuntu opens a windows partition out of the box. To see the ubuntu partition from XP you can install ext2fs which will sit on the windows control panel.

[http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html)

---

### Post by behindtheeye on 2008-05-30
Sounds good thanks! If I want to make a partition on my new drive to store documents, videos & music (would this be /home ?) accessible by Windows and Ubuntu, is there a way I can do this so it can be read natively by both OS's instead of using ext2fs?

---

### Post by didac on 2008-05-30
If you don't want to follow the ext2fs, then from Windows delete the partition you created, create a new partition, which is not using the whole hard disk, and format it. Then install Ubuntu in the empty space of your new hard disk. Your windows partition will be mounted in /media Leave it there.

There are other ways of doing this. This is simple.

---

### Post by zvacet on 2008-05-30
@ **behindtheeye**

You can make another partition beside root and home and name it for example **storage**.On that partition you will put your music...Format that partition as fat32 and both OS will read it nativly.But I don´t see anything wrong with using ext2fs.If you decide to use  **ext2fs** you need only root and home partition (and of course swap but that is not issue here),and put all your files on home partition.If I said something wrong feel free to correct me.

---

