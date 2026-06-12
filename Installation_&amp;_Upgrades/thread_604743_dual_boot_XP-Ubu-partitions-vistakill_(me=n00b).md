---
title: "dual boot XP-Ubu-partitions-vistakill (me=n00b)"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by ubu-lemon on 2007-11-06
I installed Ubuntu 7.04 on a pre installed Vista laptop,
I chose the automatic way to partition the HDD but I don't know what it actually did (that's because I'm so new to all this of course)

If I do *sudo fdisk -l *,
i get this : 
[I]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1045     8393931   27  Unknown
/dev/sda2            1046       12826    94630882+   7  HPFS/NTFS
/dev/sda3           12827       19180    51038505   83  Linux
/dev/sda4           19181       19457     2225002+   5  Extended
/dev/sda5           19181       19457     2224971   82  Linux swap / Solaris[/I]


also when starting up, Grub still proposes me Linux or Vista, although i thought Vista would be dead,and  i don't see it in this list.

Now there is no way I'd want Vista back (ever!), but I'm planning to dual boot my computer with XP. Also I'd like it to be on the same space Vista used to have (which was more than 40 GB !!!)
but do not know how I should do this?

---

### Post by bulldog on 2007-11-06
The best way to do this is to use the Gparted live cd.
Remove all partitions from the hdd so there is only unallocated space left.
Create a primary partition for your XP install [40GB]
Create a 10GB partition for your / [root] system ext3
Create a 1 or 2GB swap partition 
Make the rest off the space /home for your personal data ext3

Install XP first in the created partition
Install ubuntu and use the / partition to mount your root filesystem
Mount swap as swap
Mount /home as /home and your done.

 
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by ubu-lemon on 2007-11-08
> **bulldog said:**
> The best way to do this is to use the Gparted live cd.
Remove all partitions from the hdd so there is only unallocated space left.
Create a primary partition for your XP install [40GB]
Create a 10GB partition for your / [root] system ext3
Create a 1 or 2GB swap partition 
Make the rest off the space /home for your personal data ext3

Install XP first in the created partition
Install ubuntu and use the / partition to mount your root filesystem
Mount swap as swap
Mount /home as /home and your done.

 
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

i'll take a look at your link (but first a little sprint to my java-lessons)
I think to read that you say that i have to start with XP first, so start it all over again,
from an empty disk, and after that re install Ubuntu?
Don't know what swap is, but maybe i'll find my answer in your link

thanks!

---

### Post by bulldog on 2007-11-08
The best way is to install windows first,becaus eif you do it otherwise ,you will lost grub and have no ubuntu loader left.[can be solved though]
swap is the same as the windows page file only linux uses a partition

---

### Post by anoopyadav on 2007-11-08
Can you please explain how i can get grub to load winxp??? I've kubuntu on my primary partition & want to install xp.

---

### Post by bulldog on 2007-11-08
Yes I can,but windows is generally installed on the first primary partition,I don't know if it will boot from the second one.
But to make windows boot you have to add something in the menu.lst
```

### END DEBIAN AUTOMAGIC KERNELS LIST


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1
```

The rootnoverify line should list the right partition your windows is located.
You can find that with a simple fdisk command

---

### Post by wwoodfo on 2007-11-11
I’m primarily a WinXP user, but I’d like to try Ubuntu. Right now I have a 7.10 CD and a 120MB hard drive. I set up my drive with five partitions (a primary and an extended with 4) and installed WinXP into the primary.

I left around 10MB for a Ubuntu in one of the extended partitions.

If my understanding of your previous posts is correct, it sounds like I need change my partitions so I have three (3) for Ubuntu.

My first question is whether I will be able to bring up Ubuntu from a partition in an extended partition with the WinXP dual boot.

If I have to set up another partition for the Ubuntu boot, can I use Gparted without wiping out my WinXP primary partition?

I’m also unclear on what type of file system to use for the Ubuntu partitions.

Thanks!

---

### Post by bulldog on 2007-11-11
> **wwoodfo said:**
> I’m primarily a WinXP user, but I’d like to try Ubuntu. Right now I have a 7.10 CD and a 120MB hard drive. I set up my drive with five partitions (a primary and an extended with 4) and installed WinXP into the primary.

I left around 10MB for a Ubuntu in one of the extended partitions.

If my understanding of your previous posts is correct, it sounds like I need change my partitions so I have three (3) for Ubuntu.

My first question is whether I will be able to bring up Ubuntu from a partition in an extended partition with the WinXP dual boot.

If I have to set up another partition for the Ubuntu boot, can I use Gparted without wiping out my WinXP primary partition?

I’m also unclear on what type of file system to use for the Ubuntu partitions.

Thanks!

Ubuntu will boot from any partition.primary or logical.
You don't have to create a separate /home,but if you want to use it for a bit longer it can be handy.
You can install ubuntu in the 10GB partition with no problem,you should have a swap though,1 a 2 GB max.
Use ext3 for the 10GB partition and swap for the swap.

---

### Post by wwoodfo on 2007-11-21
Thanks! I set up two (2) 10GB partitions and one (1) 2 GB partitions and have Ubuntu 7.10 installed and running.

The only problem remaining is that I would like to primarily run WinXP, and the default OS is Ubuntu.

Is there something I can do to have the WinXP multiple OS selection run at start-up with WinXP as the default OS?

TIA

---

