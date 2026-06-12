---
title: "Repartitioning hard drive"
date: 2017-11-09
forum: Installation &amp; Upgrades
---

### Post by rlongfield on 2017-11-09
Hey All,

I have a server running 14.04 that I would like to update to 16.04. It seems that back when I started way back in oh 10 or 12 10 GB was plenty of space for /.

/ is sitting on sda1
 swap is on sda 5
 home is on sda6

Is there a way to take some space from home and give it over to / without borking my system or the contents of /home?

Thanks,

---

### Post by ajgreeny on 2017-11-09
Without knowing the exact situation it is a bit difficult to know how to proceed, but one thing I can be sure of, is that your swap, sda5, and home, sda6, partitions are both logical partitions within an extended partition, probably sda2.

Because you are going to have to shrink your /home partition and move or resize the rest, I suggest using gparted from a live system as the easiest way, prior to your upgrade/reinstall.

You have to use a live system to do this and I believe that to keep all your /home files it will be easiest to boot to a live system, delete the swap partition completely (you will need to right click in it first in gparted and choose "swapoff" as it will be in use by the live OS).

Once you have deleted that, and depending on its size, you may be able to shrink the extended partition and remove the space used by your old swap partition, then extend the root partition into the now free space just to the right of the / partition.

Finally you will need to create a new swap partition at the far left hand end of the extended partition by shrinking the /home partition to the size of swap you want, which is less risky shrinking from the right hand end of a partition as the start point will remain the same.

Before doing any of this a screenshot of the gparted window from a live system would be extremely helpful and probably a lot less confusing to us all as we will be able to see the partition layout and sizes much more easily.

---

### Post by rlongfield on 2017-11-09
I can certainly take a screen shot. I might be able to do that tonight. 
I was able to free up enough space to perfrom the upgrade so I'll have to wait until that completes

---

