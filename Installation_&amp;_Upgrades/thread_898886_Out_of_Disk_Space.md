---
title: "Out of Disk Space"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by Wickd on 2008-08-23
Hi there. I am relatively new to Linux and might have made a very stupid mistake.

I was unaware of the fact that linux stores all of its applications under the root files, unlike windows where you could specify where to install it. Must I increase the size of my root partition or is there a way of having it installed in my larger partition?

I have a 250 gb hd with the following primary partitions set up
1) 6 gb - Win xp (NTFS)
2) 2 gb - Linux root (ext3)
3) 1 gb - Swap
4) 240 gb general storage

Now is there a method whereby I can install all ap[plications in a apps folder on my general storage? Or must I resize my partition using the Ubuntu partitioner? And if I do resize is there a way that I can backup the whole root directory on a second drive and then copy it back over if the root directory gets corrupted with the resize?

Thank you in advance

Oh and sorry if I posted it twice, but did not really know under which category to place this message :)

---

### Post by Pumalite on 2008-08-23
Let's see if you can increase your 'root'. Post a screenshot of Gparted.

---

### Post by prshah on 2008-08-23
> **Wickd said:**
> 
Must I increase the size of my root partition or is there a way of having it installed in my larger partition?

I have a 250 gb hd with the following primary partitions set up
1) 6 gb - Win xp (NTFS)
2) 2 gb - Linux root (ext3)
3) 1 gb - Swap
4) 240 gb general storage



1) Yes, you can resize your root partition with no data loss (excepting gremlins).

2) You need to boot off a live CD and use gparted (System-Administration-Partition Editor)

[INDENT]a. Right click each partition shown in the partition editor and choose "unmount" if it's available. For swap, choose Swapoff
b. Now resize your "general storage" partition to leave space at the _beginning_
c. Now either move or delete and recreate your swap to/at the end of the free space. (Moving is recommended)
d. Now grow (resize) your linux partition (I suggest a size of at least 15Gb)[/INDENT]

3) All drives show up under the "/" filesystem; so no, you can't install programs elsewhere (Actually you can, but it's complicated, and not worth the aggravation).

4) As for backing up your linux partition for later restoration, try using partimage. To install, open a terminal (Applications-Accessories-Terminal) and give the command ```
sudo apt-get install partimage
``` (You will need either internet access in your installed Ubuntu or the Ubuntu installation CD). Or you can use the builtin "dd" command by following [this discussion.]("http://ubuntuforums.org/showthread.php?t=874643")

---

### Post by Wickd on 2008-08-24
Thank You very much! Got it moved to 16 gb thx alot

---

