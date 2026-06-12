---
title: "root partition cannot be the first one!?"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by _teo_ on 2006-09-27
Hi all,

I reinstalled my system. During installation process I noticed strange (at least to me) behaviour. Here are the details:

1) booted from Ubuntu 6.06 CD (64-bit)
2) partitioned the drive with gparted - the very first partiotion is primary and I intended to install there. After it comes an extended one. Inside that extended partition there are some logical partitions and the last one was intended for swap
3) then I launched the installation and went to final step where I manually set that the root "/" should be the first partition and set the swap as well
4) there is a summary for the actions which will be taken during installation process and there I saw only the swap partition listed to be reformated although I set the reformat flag for both the root and swap partitions
5) the final effect is that installation process complains that no root partition is set and returns again to the partition manager

I tried different approaches and finally got it working - I had to put the swap partition in front of all the rest partitions, so that the root isn't the first one. Installation process went smooth and now I am writing from my fresh reinstalled system.

I tried to search Launchpad for similar bug(s), but I cannot find where the search function is. Also I searched the forums and found nothing. If this is a known bug, can anyone point me to it, so I can describe there my observations as well.

Thanks.

---

### Post by wieman01 on 2006-09-27
Not sure if this is a know bug, but I formated all partitions manually before I installed Ubuntu (ext3, swap). Ubuntu would not let me install it otherwise.

It does not matter where the /[root] partition sits as long as the system knows where it is.

---

### Post by _teo_ on 2006-09-28
> **wieman01 said:**
> Not sure if this is a know bug, but I formated all partitions manually before I installed Ubuntu (ext3, swap). Ubuntu would not let me install it otherwise.

This is what I did as well. All partitions were formated.

> **wieman01 said:**
> 
It does not matter where the /[root] partition sits as long as the system knows where it is.
It should be this way, but in fact I had troubles. Somehow although I manually set the root partition, it wasn't recognized in installation.

One thing I forgot to mention is that I tried automated installation in my attempts to solve the problem. This works. The whole disk was splitted in two partitions - root (primary one) and extended one (here as a logical partition was located the swap). The root partition was first one in the disk.

---

