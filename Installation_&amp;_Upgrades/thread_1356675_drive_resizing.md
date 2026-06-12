---
title: "drive resizing"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by alimooghashang on 2009-12-16
Hi all
i have both windows and ubuntu togather.
now i want to resize my ubuntu drive (sda9)
how it's possible to resize it without getting files damaged.
thanks

---

### Post by phillw on 2009-12-16
> **alimooghashang said:**
> Hi all
i have both windows and ubuntu togather.
now i want to resize my ubuntu drive (sda9)
how it's possible to resize it without getting files damaged.
thanks

Yes, it is - But it NOT recommended. I've never has a problem, but I ALWAYS have a backup. -- Muphy's Law applies !!

Regards,

Phill.

---

### Post by alimooghashang on 2009-12-16
> **phillw said:**
> Yes, it is - But it NOT recommended. I've never has a problem, but I ALWAYS have a backup. -- Muphy's Law applies !!

Regards,

Phill.
how to resize it?
i have resized it via windows and partition manager, and my files seems to be lost one upon a time.
and now i want to do it in linux without getting file lost.
thanks

---

### Post by Grenage on 2009-12-16
Use gparted, it's easiest if you do this from a live CD ( you can't resize a mounted partition).

---

### Post by phillw on 2009-12-16
Can you post the output of ..

```
sudo fdisk -l
```

and 

```
df -ah | grep dev
```

Along with a quick explanation of what they are & which you want to expand (sda9) and from where we are taking the room from.

Phill.

---

### Post by alimooghashang on 2009-12-21
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7758e15e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       19457   135805477+   f  W95 Ext'd (LBA)
/dev/sda5            2551        7064    36258673+   7  HPFS/NTFS
/dev/sda6            7065       10198    25173823+   7  HPFS/NTFS
/dev/sda7           10199       14003    30563631    7  HPFS/NTFS
/dev/sda8           14004       17998    32089806    7  HPFS/NTFS
/dev/sda9           17999       18247     2000061   82  Linux swap / Solaris
/dev/sda10          18248       19457     9719293+  83  Linux
```

Hi this is the out put
i want to resize sda10 which linux is installed and make it bigger.


```
/dev/sda10            9.2G  7.2G  1.6G  83% /
udev                  501M  292K  501M   1% /dev
none                     0     0     0   -  /dev/pts
none                  501M  612K  501M   1% /dev/shm

```

---

### Post by raymondh on 2009-12-21
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

- Back-up
- Use a liveCD and in live session (TRY UBUNTU...) access gparted from system > admin > partition editor
- Double check partitions are unmounted by right clicking on it/them and if given the option to unmont, do so.  For swap, use swapoff.

Remember, resize/enlarge the extended partition first before resizing/enlarging the logical.

EDIT : where do you plan to get the space?

---

### Post by alimooghashang on 2009-12-21
I didn't plan it yet
I want to get it from other drives and make the ubuntu drive bigger.
please tell me which drive i should resize first and then... and so on
thanks

---

### Post by raymondh on 2009-12-21
> **alimooghashang said:**
> 
please tell me which drive i should resize first and then.

What partition (or drive,as you refer it to) to resize first depends on WHAT PARTITION YOU WISH TO TAKE SPACE FROM TO GIVE TO UBUNTU.

Sda1 must be your windows
sda2 could be a recovery partition
The rest are logical partitions inside an EXTENDED.   

-Decide where to get the space from
-Read the link I gave earlier
-Back-up

Nevertheless, defrag those NTFS partitions first.

---

### Post by darkod on 2009-12-21
> **raymondh said:**
> 
Sda1 must be your windows
sda2 could be a recovery partition
The rest are logical partitions inside an EXTENDED.   



Just to add, /dev/sda2 IS the extended.
We can not choose for you which partitions to delete or shrink (because that's the only way you can make space). Also you have to keep in mind that you can only expand /dev/sda10 if the free unallocated space is NEXT TO IT! To the left, or right, but next to it.

---

### Post by raymondh on 2009-12-21
> **darkod said:**
>  Also you have to keep in mind that you can only expand /dev/sda10 if the free unallocated space is NEXT TO IT! To the left, or right, but next to it.

If you decide (as an example only) to take space from sda5 and shrink that partition, what darko means is that you have to move sda6,7,8 and 9 to make the unallocated space beside sda10.

---

