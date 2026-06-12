---
title: "oh no =( all my music...BUT I KNOW ITS THERE!"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by thesanders on 2008-02-15
Hey everyone! so, here's the deal.

i'm dual booted and i have 2 HDs, my original HD (250gb) has Vista installed on it (yea yea boo vista), 2nd HD (500 gb) jus got ubuntu installed on it (yay ubuntu). now here's the thing, before i installed ubuntu on my 2nd HD, i had many files on the HD, such as programs, apps, music (lots of music), vids, etc. now, the thing is, when i boot up vista, my G drive (the 2nd HD) shows up as a CD drive that I cannot access and it says "please insert a disc into the G: drive". and i'm not really sure how to get these files through ubuntu since i'm relatively new to it.

is there anyway to get my music back? :(

thanks peeps :guitar:

---

### Post by drummingpariah on 2008-02-15
So, you had many files on your second hard drive, then reformatted that drive (erasing all of it) and installed Ubuntu over it.  Do I have that right?

I'm sorry, but if that's an accurate description of what's been done, all your files are lost.  It is now an XFS partition (most likely) and everything's wiped out.  At least you have Ubuntu now, though right?

---

### Post by forestpixie on 2008-02-15
open a terminal in ubuntu and do this - terminal is in apps> accessories, post the output, then we can see what's going on.

```
sudo fdisk -l
```

it'll ask for your password - put it in but you won't see it *** you type, it's hidden

---

### Post by thesanders on 2008-02-15
sorry!! i completely forgot to include the obvious, no i didn't format my HD before installing ubuntu, i resized free space that i had on it.

the output of fdisk -l is the following:

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7        1312    10485760    7  HPFS/NTFS
/dev/sda3   *        1312       30394   233604096    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b2bfa36

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       47567       60257   101940457+  83  Linux
/dev/sdb2               1       47566   382065862+  83  Linux
/dev/sdb3           60258       60801     4369680    5  Extended
/dev/sdb5           60258       60801     4369648+  82  Linux swap / Solaris

---

### Post by forestpixie on 2008-02-15
the second hdd is completely formatted to ext3 and linux swap - there are no ntfs partitions there. I assume that you accessed them previously through vista, in which case there would be a ntfs partition - assuming that you haven't used the drive since you might be able to rescue something with [photerec]("http://www.cgsecurity.org/wiki/PhotoRec") 

But I would be inclined to think along the lines of restoring from the backups

It would appear that you chose the wrong option when you installed ubuntu

you could check with gparted - system >admin >partition editor - see what that shows you but it doesn't look good to me

---

