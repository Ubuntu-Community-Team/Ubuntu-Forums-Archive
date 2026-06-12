---
title: "Avoid filesystem check at startup"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by xlinuks on 2007-04-30
Hi,
Is it possible, if so then how, to skip the filesystem check (I guess it's the 'fsck' app) during (K)Ubuntu startup? I have never had issues with my HDD, so I'd really appreciate a hint how to turn this off. It takes half of the system boot time.
Forgotten to mention, I have KUbuntu 7.04 in case there's any difference in doing this between Ubuntu and KUbuntu.

---

### Post by bulldog on 2007-04-30
The file system check should only occur every 30th time you boot.
Not every time,it has a function,so why turn it off?

What kind of file system do you use? ext3 is the native for ubuntu FYI.

---

### Post by xlinuks on 2007-04-30
KUbuntu is on reiserFS for sure, and a few other partitions. I really want to turn it off cause for some reason it checks the FS every time I oot but I never had issues with the FS nor with the HDD. Since I installed KUbuntu 7.04 everything is kept with default settings. Here's a screenshot of KUbuntu loading:
[http://www.geocities.com/xlinuks/pub/feisty_startup.jpg](http://www.geocities.com/xlinuks/pub/feisty_startup.jpg)

---

### Post by bulldog on 2007-04-30
Well I can give you an amount of commands you can use,picked them up on my journey's on the net.
But can't tell you what they actual do or not.
So,basically,use them on your own risk!!
```
Hdd check disable:
sudo tune2fs -c 0 -i 0
Hdd check change from 30 to 50:
sudo tune2fs -c 50 /dev/hdx@
To see the actual settings:
sudo dumpe2fs /dev/whatever
fsck : check and repair a Linux file system
dosfsck : check and repair MS-DOS file systems
e2fsck : check a Linux ext2/ext3 file system
expiry : check and enforce password expiration policy
fsck.ext2 : check a Linux ext2/ext3 file system
fsck.ext3 : check a Linux ext2/ext3 file system
fsck.minix : a file system consistency checker for Linux
fsck.msdos : check and repair MS-DOS file systems
fsck.reiser4 : the program for checking and repairing reiser4 filesystem.
fsck.reiserfs : The checking tool for the ReiserFS filesystem.
fsck.vfat : check and repair MS-DOS file systems
hpfsck : check integrity of an HFS+ volume
reiserfsck : The checking tool for the ReiserFS filesystem.
xfs_check : check XFS filesystem consistency
```

---

### Post by lukew on 2007-04-30
> **xlinuks said:**
> Hi,
Is it possible, if so then how, to skip the filesystem check (I guess it's the 'fsck' app) during (K)Ubuntu startup? I have never had issues with my HDD, so I'd really appreciate a hint how to turn this off. It takes half of the system boot time.
Forgotten to mention, I have KUbuntu 7.04 in case there's any difference in doing this between Ubuntu and KUbuntu.

The last column is the fsck check option. 

Change it gfrom 2 to 0

```
/dev/hda2  	/  	ext2  	defaults  	1 1
/dev/hdb1 	/home 	ext2 	defaults 	1 0
```

---

### Post by bulldog on 2007-04-30
> **lukew said:**
> The last column is the fsck check option. 

Change it gfrom 2 to 0

```
/dev/hda2  	/  	ext2  	defaults  	1 1
/dev/hdb1 	/home 	ext2 	defaults 	1 0
```

Completely disable the fsck shouldn't be wise to do.
It's there for a purpose,making it 50 instead of 30,well,I can live with that,but not completely disable the fsck.

---

### Post by lukew on 2007-04-30
> **bulldog said:**
> Completely disable the fsck shouldn't be wise to do.
It's there for a purpose,making it 50 instead of 30,well,I can live with that,but not completely disable the fsck.

Thats all very well but that is not what he asked for. Please don't shot the messenger, who incidentally has all his file systems checked every 30 boots.

---

### Post by bulldog on 2007-04-30
> **lukew said:**
> Thats all very well but that is not what he asked for. Please don't shot the messenger, who incidentally has all his file systems checked every 30 boots.

Okay,I won't shoot you :) 
I quoted your message as a warning for TS to not disable it completely.

I know what he asked for,but when things are messed up,ubuntu is to blame as usual, not TS.

---

### Post by xlinuks on 2007-04-30
I'm not sure what you mean. Should I edit /etc/fstab and change 2 to 0 say:
> 
# /dev/sdb3
UUID=0d44c876-6387-4457-a624-16cfa9bd99f3 /media/sdb3     reiserfs defaults        0       2

to
> 
# /dev/sdb3
UUID=0d44c876-6387-4457-a624-16cfa9bd99f3 /media/sdb3     reiserfs defaults        0       0

?

---

### Post by bulldog on 2007-04-30
Yes,you can do that for every reiserfs partition.

**But keep in mind your partitions are never checked anymore,you should do this manually**

---

### Post by xlinuks on 2007-04-30
Wow! I did it and I'm very satisfied!
Now I have the computer booting only about 30 seconds instead of about 60!!!
thanks a lot  !! :)
You may wonder why I'm so happy, it's just because my friends kept asking why Linux is so slow at booting while windows does it much faster and I had nothing to answer.

---

### Post by bulldog on 2007-04-30
> **xlinuks said:**
> Wow! I did it and I'm very satisfied!
Now I have the computer booting only about 30 seconds instead of about 60!!!
thanks a lot  !! :)
You may wonder why I'm so happy, it's just because my friends kept asking why Linux is so slow at booting while windows does it much faster and I had nothing to answer.


Don't forget to check the file system now and then!!

And congrats with your success :guitar:

---

### Post by xlinuks on 2007-04-30
I won't forget, I'll only check it once a week or a month, I have an UPS and new HDDs so there's few chances that the FS might get screwed. I never had any issue within months nor with Mandriva and now with KUbuntu either :)

---

