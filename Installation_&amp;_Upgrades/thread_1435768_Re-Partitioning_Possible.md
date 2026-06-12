---
title: "Re-Partitioning Possible"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by Iokua86 on 2010-03-21
Ok. I just realized that this could be a Dumb move. But, When I installed UBUNTU 9.10 I used all my disk space. I just realized that I have no free space! Is there a way to repartition the system without reinstalling the entire thing?

---

### Post by raymondh on 2010-03-21
> **Iokua86 said:**
> Ok. I just realized that this could be a Dumb move. But, When I installed UBUNTU 9.10 I used all my disk space. I just realized that I have no free space! Is there a way to repartition the system without reinstalling the entire thing?

why not just resize and create the free space you want?

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)


As always, have a working/tested back-up of your files.

Best,

raymond

---

### Post by wilee-nilee on 2010-03-21
> **raymondh said:**
> why not just resize and create the free space you want?

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)


As always, have a working/tested back-up of your files.

Best,

raymond

Thats a old link although it is correct just a long read.


Op boot the live cd go to gparted in system applications the turn off swap by right clicking on it and turning off then you can resize the partition.

---

### Post by Iokua86 on 2010-03-29
wow, it was hard navigating back here (says the newbie). I'm not exactly what  sure what all this means. I don't have G-parted but there is a disk utility that comes with ubuntu, that allows me to repartition. The only issue now is that there's a  device that's stopping me from doing so ./dev/sda1 apparently is mounted and I don't know how to unmount it.

---

### Post by drs305 on 2010-03-29
The disk utility is most likely gparted, but you may see it in the menu as "Partition Editor". If you are referring to "Disk Utility/palimpest" then the following won't apply (unless you start using Gparted).

If it is Gparted/Partition Editor:

To unmount a partition, click on either the graphic in the upper panel or select the partition in the lower pane (sda1). Then from the upper menu, select "Partition, Unmount". 

Any partition with a "key" icon in the lower pane is mounted and should be unmounted. There is also probably a "swap" partition that is also mounted. To unmount the swap partition, select it, then "Partition, Swapoff".

---

### Post by Slim Odds on 2010-03-29
> **drs305 said:**
> ...

If it is Gparted/Partition Editor:

To unmount a partition, click on either the graphic in the upper panel or select the partition in the lower pane (sda1). Then from the upper menu, select "Partition, Unmount". 
...

If he put everything in one partition, he will not be able to unmount that partition (because Ubuntu is running from that partition). It's much better to just use the LiveCD. That way there is no need to unmount anything (or turn off swapping either).

---

### Post by Iokua86 on 2010-03-29
what's the LiveCD? and where can I get it?

---

### Post by Iokua86 on 2010-03-29
it is the Palimpsest Utility btw.:-?

---

### Post by Slim Odds on 2010-03-29
> **Iokua86 said:**
> what's the LiveCD? and where can I get it?

The default download is the Live CD. The alternate CD is not a Live CD.

The default CD is bootable in any system that can boot from CD.

---

### Post by drs305 on 2010-03-29
> **Slim Odds said:**
> It's much better to just use the LiveCD. That way there is no need to unmount anything (or turn off swapping either).

Actually, even when using the LiveCD, a swap partition is created and would need to be unmounted if wiping out all the partitions.

---

### Post by Slim Odds on 2010-03-29
> **drs305 said:**
> Actually, even when using the LiveCD, a swap partition is created and would need to be unmounted if wiping out all the partitions.

Not true. When running from the LiveCD it's all memory. It does not touch the hard drives.

That's actually **the** reason for the LiveCD (even though you can install from it). It lets you try Ubuntu without having to do anything to your existing system. As long as you can boot from CD, you can run Ubuntu entirely in RAM.

---

### Post by drs305 on 2010-03-29
> **Slim Odds said:**
> Not true. When running from the LiveCD it's all memory. It does not touch the hard drives.

That's actually **the** reason for the LiveCD (even though you can install from it). It lets you try Ubuntu without having to do anything to your existing system. As long as you can boot from CD, you can run Ubuntu entirely in RAM.

Yes, you can run Ubuntu in RAM. But if you look at Gparted running in the LiveCD, it shows a swap partition and that partition is mounted. I will have to play with it some more.  It appears to use an existing swap partition if found; I believe it must be umounted for Gparted to perform operations on some of the partitions.

---

### Post by raymondh on 2010-03-29
> **drs305 said:**
>  it appears to use an existing swap partition if found; i believe it must be umounted for gparted to perform operations on some of the partitions.

+1

---

### Post by Slim Odds on 2010-03-29
Ok, so turn off swap and continue......

---

