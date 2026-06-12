---
title: "Reclaim disk space by removing Kubuntu"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by cogier on 2011-10-23
I run Ubuntu 10.04 and I have installed Kubuntu 11.10 as a dual boot. I can't get Kubuntu to boot. 

There are no other operating systems on the computer.

How can I remove Kubuntu and claim back the disk space it is using without destroying my existing Ubuntu 10.04 installation? 

Thanks.

---

### Post by zvacet on 2011-10-23
You can do it with ubuntu live CD and program named Gparted.Just delete Kubuntu partition and after that you can resize your ubuntu on unallocated space or make new partition you will use with Ubuntu.When you are finish from Ubuntu run

```
sudo update-grub
```

---

### Post by cogier on 2011-10-23
Thanks, zvacet but GParted shows 7 items (see attached).
Which should I delete?

---

### Post by jerrycal on 2011-10-23
> **cogier said:**
> Thanks, zvacet but GParted shows 7 items (see attached).
Which should I delete?


dev/sda6. It's 322GB partition with only 8GB used, and dev/sda7 s well. Also, you don't really need so much Swap space. Usually 2GB is plenty.

---

### Post by cogier on 2011-10-24
Can you confirm that I should Delete sda6 and sda7 then resize sda1 to take up the slack?

Thanks,

---

### Post by jerrycal on 2011-10-24
> **cogier said:**
> Can you confirm that I should Delete sda6 and sda7 then resize sda1 to take up the slack?

Thanks,

Yes, dev/sda6 seems like has nothing on it besides the OS since it only has 8GB used.
dev/sda1 has 268GB used so that must be your main system. 

OK, do this. Boot Ubuntu and open your Nautilus window. It should tell you how much space you have left. If it tells you you have 329GB left you know you're on dev/sda1 and you need to keep that one. 
Regardless, you should have a backup just in case something goes wrong. 

In gparted, do one operation at a time. Meaning. Remove dev/sda6, when its done, remove dev/sda7, when it's done, reclaim the free space.

---

### Post by cogier on 2011-10-25
Thanks for the help jerrycal.

I have managed to delete sda6 and sda7. This caused all sorts of GRUB problems that have taken sometime to sort out but are sorted now.

I can't seem to reclaim the "Unallocated" space. (See attached). I have tried this from a live CD but I can't see how to do it.

Any advice appreciated.

---

### Post by jerrycal on 2011-10-25
> **cogier said:**
> Thanks for the help jerrycal.

I have managed to delete sda6 and sda7. This caused all sorts of GRUB problems that have taken sometime to sort out but are sorted now.

I can't seem to reclaim the "Unallocated" space. (See attached). I have tried this from a live CD but I can't see how to do it.

Any advice appreciated.


Are you running gparted from LiveCD? 
Try not to stretch the partition all the way. You may need to leave some space there.

---

### Post by critin on 2011-10-25
Would the extended partition need to be deleted first?
Just curious.

---

### Post by cogier on 2011-10-28
Thanks for the replies: -

jerrycal
Yes I am running GParted from a Live CD, I thought that doing this would mean I could work on the unmounted drive but as you can see for some reason the extended partition is mounted but /sda1 is not!

critin
I am unable to delete the extended partition, I presume, for the same reasons as above.

It's all very confusing! ](*,)

---

### Post by critin on 2011-10-28
Your swap is inside the extended partition.  Can you unswap the swap partition?  Right click on partition 5 and see if you can click 'unswap' or whatever the wording is.  If you can do that, you can then delete the extended and use the empty space.
Un swap is unmounting that partition.

---

### Post by zvacet on 2011-10-28
Delete swap partition.

---

### Post by cogier on 2011-10-29
Thanks again critin

The command is "Swapoff" which enabled me to delete the Swap and the extended partitions. Then I was able to extend /sda1 to fill the void.

There is now no Swap area, as I have 4GB of memory and have never seen this area in use I shall see how things progress.

Thanks to all for your help. O:)

---

### Post by critin on 2011-10-29
lol, unswap--swapoff: semantics.  I'm glad you got it done!

---

