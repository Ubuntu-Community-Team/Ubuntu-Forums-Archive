---
title: "mounting a disk &quot;unallocated&quot;"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by lovo on 2011-08-04
Hi folks,

Im trying to recover my second disk that disappear when I reinstalled ubuntu.
I have 1 disk where I installed windows + ubuntu : /dev/sdb

and another disk of data that is not recognized in nautilus, I only see it in gparted:
[IMG]http://img13.imageshack.us/img13/5066/screenshotwa.png[/IMG]

There is data on it I would like to recover! Is it possible ?

---

### Post by Hakunka-Matata on 2011-08-04
Look at post # 2 in [http://ubuntuforums.org/showthread.php?t=1798473&highlight=recover+partition](http://ubuntuforums.org/showthread.php?t=1798473&highlight=recover+partition)

---

### Post by YesWeCan on 2011-08-04
Would you post the output of
[COLOR="Navy"]sudo sfdisk -luS[/COLOR]

---

### Post by lovo on 2011-08-05
Thanks for the replies!

> **Hakunka-Matata said:**
> Look at post # 2 in [http://ubuntuforums.org/showthread.php?t=1798473&highlight=recover+partition](http://ubuntuforums.org/showthread.php?t=1798473&highlight=recover+partition)

Ok, I will try, Im however slightly afraid that this software doesn't work for ext4 partition as it's only mention ext2/3 in the doc (like many softs I have found).


> **YesWeCan said:**
> Would you post the output of
[COLOR="Navy"]sudo sfdisk -luS[/COLOR]

```
Disk /dev/sda: 48641 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1             0         -          0   0  Empty
/dev/sda2             0         -          0   0  Empty
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty

Disk /dev/sdb: 19457 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *        63  81920159   81920097   7  HPFS/NTFS
		end: (c,h,s) expected (1023,254,63) found (1023,239,63)
/dev/sdb2      81922046 312580095  230658050   5  Extended
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty
/dev/sdb5      81922048 308674559  226752512  83  Linux
/dev/sdb6     308676608 312580095    3903488  82  Linux swap / Solaris
```

Im trying to recover data from my 400GB hard disk, the other 160GB hard disk seems to be perfectly recognized and working.

I don't understand this output. I though sdb was the smaller disk .. but sdb5/6 go up to 300GB .. ?

---

### Post by YesWeCan on 2011-08-05
The sizes are in 512 byte sectors so sdb is your 160GB disk.
Your 400GB disk seems to have no entries in its partition table. Any idea what might have caused this?

---

### Post by lovo on 2011-08-05
> **YesWeCan said:**
> The sizes are in 512 byte sectors so sdb is your 160GB disk.
Your 400GB disk seems to have no entries in its partition table. Any idea what might have caused this?

ah, that's a block number, ok.

Yes, there are reasons, I have made a mistake when I reinstalled. I installed the last ubuntu on the same partition as the previous one, then the grub was lost. I used a program to recover the grub and that's when my second disk got lost.

Im using the method of Hakunka-Matata, the search takes very long time... look over all cylinders.

The data seems to be found, and Im optimist as I haven't deleted nor overwritten anything.

Will see!

---

### Post by lovo on 2011-08-05
After many tries, it doesn't look so good ..
When I analyse the disk in deep, it says:
[IMG]http://img26.imageshack.us/img26/1471/31737572.png[/IMG]

Then if I do continue :
[IMG]http://img4.imageshack.us/img4/5969/68301200.png[/IMG]

It means I can only recover this small part of the disk ?

---

### Post by lovo on 2011-08-07
Hey, Im still stuck with this problem. Any idea ?

---

