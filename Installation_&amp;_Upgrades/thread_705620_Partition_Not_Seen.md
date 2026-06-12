---
title: "Partition Not Seen"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by AbsentHarvest on 2008-02-23
I have resized my main partition (Windows).
With the unallocated space. (Aproxmately 13GB)
I turned it into a partition. (U:/ for Ubuntu)
I booted into the Ubuntu CD and installed.
The problem i'm getting is that it won't let me install it into that partition.
I'm guessing because this U:/ is the 5th partition inside the 4th partition.
However, nothing is in the 4th partition but 1MB of unallocated space and my U:/
How can I correct this?

---

### Post by wolfen69 on 2008-02-23
im confused. is U:/ the name you gave the partition?

---

### Post by Pumalite on 2008-02-23
You are allowed 4 primary partitions per drive
Post sudo fdisk -lu

---

### Post by AbsentHarvest on 2008-02-23
Well, in Windows.
It looks like this.
[[IMG]http://img405.imageshack.us/img405/6973/18967176pt7.th.jpg[/IMG]](http://img405.imageshack.us/my.php?image=18967176pt7.jpg)
I would show you what I see in Ubuntu only I can't connect to the internet with it currently.
In Ubuntu... It shows..
I can't remember the specific information.

1...
2...
3...
[-] 4...
- 1MB Unallocated
- 5 (Ubuntu)

So basically, I'm taking an educated guess that somehow... the 4th partition didn't delete right and the partition I made is inside that partition, it can't get through, because the unallocated space in the 4th partition alone is 1MB, and that's what it's seeing.  You know what I mean?

---

### Post by Rocket2DMn on 2008-02-24
You have to reformat that "U:" drive from the Ubuntu CD when you install to an ext3 filesystem.  Linux doesn't use NTFS natively.  You will need to reinstall, selecting to format that partition with your root partition (ext3) and your swap partition (swap).

---

