---
title: "Installing 10 in NTFS primary"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by MeCasa on 2010-05-30
I've had 8.04 installed in a 10 gb NTFS Primary partition with XP installed as my main OS in C:various times and now I have a new comp and set it up with my 7 standard partitions

Factory Recovery FAT 32
XP (C) NTFS Primary
Ubuntu NTFS Primary
APPS NTFS logical
FILES NTFS logical
MEDIA NTFS logical
BACKUP FAT logical

I wanted to install ubuntu to play around again but I can't get 10 to install and I'm not sure what I'm doing wrong. I get to the screen asking which partition to install in and after highlighting the partition I hit forward and get the 'No root files" prompt. I don't remember using Change/Delete or Revert but it's been awhile.

What am I doing wrong? I have my C Drive iso'd in BACKUP but I'd rather not screw up my machine as this is my work machine and I'm busy. So, I thought I'd come for advice as I've already locked up the machine and the DVD when I tried installing from a 9.1 disk

What am I doing wrong?

Thanks
MeCasa

PS: My apologies if this has been asked a thousand times

---

### Post by darkod on 2010-05-30
Are you trying to install wubi inside windows, or proper ubuntu on its own partition?

The screen you are describing sounds like the ubuntu installer. Ubuntu can't install on ntfs. I guess earlier you always used wubi inside windows.

You need a ext3/ext4 partition instead of ntfs, and also usually a smaller swap partition too.
And if trying to use already existing partition, you do need to use the Change button and set the filesystem, mount point and the format box (if you want to format the partition) properly.

---

### Post by MeCasa on 2010-05-30
I had Ubuntu installed in its own partition with a dual boot with winders and I don't know why I thought it was installed in NTFS, but I did and it wasn't.

I think I remember now but is there a good tutorial since I also thought I remembered Ubuntu installed in NTFS. :P

A). Old age?
B). Too much bourbon?
C). Too much THC?
D). All of the above

It'd probably D, but I'm really not in the mood for re-learning by error so help me find a good tutorial

Thanks for the help

---

### Post by darkod on 2010-05-30
I have this bookmarked:
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

The screenshots are from 9.10 but 10.04 is similar if not identical in all screens.

---

### Post by MeCasa on 2010-05-30
Thank you sir

---

