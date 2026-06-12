---
title: "Cloning hard drive"
date: 2011-10-02
forum: Installation &amp; Upgrades
---

### Post by Timothy Taylor on 2011-10-02
I have an interesting problem.

I recently upgraded from 80Gb to 250Gb HDD in my netbook using:
```

dd if=/dev/sda of=/dev/sdb bs=64k conv=notrunc,noerror

```
and using *gparted* to expand the partition afterwards.

This worked perfectly.

I found that the new HDD used much more power than the old HDD, reducing run time to an unacceptable level.

I bought a 128Gb SSD, with which to replace the new HDD.
I used gparted to shrink the partition from 250Gb HDD to 120Gb, and recreated the extended/swap partitions.

I then used dd to copy this image to the new SSD.
This *seemed* to work: the netbook boots fine and all works well, except when I try to use gparted to expand the partition to the full 128Gb.  Gparted reports all the space on the SSD as "unallocated", even though Disk Utility shows the 120Gb ext4 & 4Gb extended/swap partitions.

I used gparted to shrink the HDD partition to around 80Gb and tried again, but the result is the same: gparted reports the entire disk as "unallocated" and I cannot expand the ext4 partition.

Any ideas?

---

### Post by howefield on 2011-10-02
Post spliced off to own thread.

---

### Post by coffeecat on 2011-10-02
> **Timothy Taylor said:**
>   Gparted reports all the space on the SSD as "unallocated", even though Disk Utility shows the 120Gb ext4 & 4Gb extended/swap partitions.

I think I know why this might be. Post the output of:

```
sudo fdisk -lu
```

... and we'll take it from there.

---

### Post by Timothy Taylor on 2011-10-02
> **coffeecat said:**
> I think I know why this might be. Post the output of:

```
sudo fdisk -lu
```

... and we'll take it from there.

OK
```

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ffb5d5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   245762369   122881153+  83  Linux
/dev/sda2       245762370   253955519     4096575    5  Extended
/dev/sda5       245762433   253955519     4096543+  82  Linux swap / Solaris

```

(This is after going back to trying to copy ~ 120Gb partition)

---

### Post by coffeecat on 2011-10-02
Hi. Here's your problem:

> **Timothy Taylor said:**
> 
```

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total [COLOR="Red"]250069680[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ffb5d5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   245762369   122881153+  83  Linux
/dev/sda2       245762370   [COLOR="Red"]253955519[/COLOR]     4096575    5  Extended
/dev/sda5       245762433   [COLOR="Red"]253955519[/COLOR]     4096543+  82  Linux swap / Solaris

```

During the cloning process back and forth, the end sector for your extended partition (and sda5 logical) has been defined as beyond the physical end of the drive. This confuses Gparted which ends up showing the whole drive as unallocated. You need fixparts:

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

That will, hopefully, fix it in a trice. Take care when you try to download it. Last time I looked the download pages are a labyrinth and also lead you to gdisk, which you most definitely do not want in this situation.

Post back if you need some help, but it's been a few months since I used fixparts, so I'm a bit rusty.

---

### Post by Timothy Taylor on 2011-10-02
> **coffeecat said:**
> Hi. Here's your problem:

(*snip*)

By Jove!  You've got it Professor!
:)

Yeah, all fixed now - tho not in a trice, due to USB drive not wanting to boot for some reason...

Thanx very much for your help.
:)

---

### Post by coffeecat on 2011-10-02
I'm glad it worked. Good luck! :)

---

