---
title: "Can't have a partition outside the disk (GParted)"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by gamecraziness on 2010-12-01
Hello,

I recently ran TestDisk to attempt to recover some files. In doing so, I created an extended partition which is eating away space from my Ubuntu partition (or at least it seems like it; I don't see how this would happen). I would like to know how to get rid of it. GParted doesn't work, and I don't want to mess with fdisk since I have limited knowledge about partitions. Here is my fdisk -l:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x998ed7f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1306    10486784    7  HPFS/NTFS
/dev/sda2            1306       36337   281381884+   7  HPFS/NTFS
/dev/sda3           36337       38785    19670016   83  Linux
/dev/sda4           38785       38914     1036980    f  W95 Ext'd (LBA)
/dev/sda5           38786       38913     1028152   82  Linux swap / Solaris

I *think* this would work, is this correct?

1. Delete sda4
2. Change the end of sda3 to 38786

If correct, how would I go about doing this? This wouldn't damage sda3, would it?

Thanks in advance.

---

### Post by efflandt on 2010-12-01
You might want to run **sudo fdisk -lu** to see which "sectors" instead of "blocks" everything starts and ends at, because it does not appear that everything is using cylinder boundaries.  And that would tell you if anything is actually overlapping. Partitions usually begin at least 1 block higher than previous one ends on unless not on cylinder boundaries, and there is at least a 63 "sector" gap at the beginning of a primary or logical partition.

And in the future, it would be a good idea to record and/or print a snapshot of **sudo fdisk -l** and **sudo fdisk -lu** before tampering with partitions.  That way you could at least put things back like they were, as long as you have not half attempted to move partitions (aborted the middle of a move).

---

### Post by dino99 on 2010-12-01
or boot on partedmagic

---

### Post by gamecraziness on 2010-12-01
Thank you very much.

Here is fdisk -lu:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x998ed7f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    20975615    10486784    7  HPFS/NTFS
/dev/sda2        20975616   583739384   281381884+   7  HPFS/NTFS
/dev/sda3       583739392   623079423    19670016   83  Linux
/dev/sda4       623079450   625153409     1036980    f  W95 Ext'd (LBA)
/dev/sda5       623081025   625137328     1028152   82  Linux swap / Solaris

It seems sda4 is extending beyond the start of sda5. Is this the problem?

Also, about PartedMagic, will this work any better than GParted from a LiveCD? Because I tried that.

Thanks in advance.

---

### Post by coffeecat on 2010-12-01
Do **not** try to delete sda4. sda4 is an extended partition which "contains" the logical partition sda5. That is completely normal. At the moment I can't see whatever problem is in your partition table that is upsetting gparted. but I will keep looking. PartedMagic will not be any better because it and gparted both rely on parted. What exactly do you mean by 'gparted won't work'?

---

### Post by Quackers on 2010-12-01
The problem appears to me to be this

```
255 heads, 63 sectors/track, 38913 cylinders, [COLOR="Red"]total 625142448 sectors[/COLOR]
```

but sda4 ends on sector [COLOR="Red"]625153409[/COLOR]

Sadly, I'm not sure what to do about it :-(

---

### Post by coffeecat on 2010-12-01
> **Quackers said:**
>  sda4 ends on sector [COLOR=Red]625153409[/COLOR]

Quackers, could you recommend a good optometrist for me? :wink:

@gamecraziness, you need to read this:

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

It describes the same problem and the fix. Have fun. :|

---

### Post by Quackers on 2010-12-01
Nice one coffeecat!

BTW looking at your avatar you won't need an optometrist if you open your eyes :-)

---

### Post by Rubi1200 on 2010-12-01
I also found something that looks very interesting:
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)

The poster who had the solution, caljohnsmith, is one of the people who helped create the boot info script we are all familiar with.

However, I cannot vouch for the solution and advise making backups in any event.

---

### Post by gamecraziness on 2010-12-01
Thank you all for the help! Coffeecat, your link worked; I have successfully gotten rid of that partition!

I have another problem now. Ubuntu is telling me I'm using 16.9 GB of my my 20 GB partition. However, I know I don't have that much data there. Disk Usage Analyzer confirms this, telling me that "/" is using 7.9 GB. How is this so? I suspect it's Photorec files that I recovered and then deleted. I used gksu nautilus to delete, but if my suspicions are correct they did not delete properly. Any idea on how to recover this space?

Thanks in advance.

---

### Post by coffeecat on 2010-12-01
> **gamecraziness said:**
> I used gksu nautilus to delete, but if my suspicions are correct they did not delete properly. Any idea on how to recover this space?

Yes. If you use a root nautilus to delete a file it will end up in root's trash. It's not physically deleted. See what's in /root/.local/share/Trash/. If I remember correctly, it will have the same files and info folders as with an ordinary user's trash - the files being in the files folder. It will be safe to delete the whole of the Trash folder and contents, either with a root nautilus* or 'sudo rm'.

**EDIT:** * use shift+delete to delete something straightaway without it going to trash.

---

### Post by gamecraziness on 2010-12-01
Yes! Saved me again. I cannot thank you enough. :D

---

### Post by coffeecat on 2010-12-02
Glad it's all sorted. That link I posted earlier came to my rescue once with a similar issue after using testdisk.

---

