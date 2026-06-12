---
title: "Where to install GRUB ?"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by Minimal Hank on 2011-05-14
I thought I should try Ubuntu on my new laptop but I'm stuck with where to install GRUB ..

```
DISKPART> LIST PARTITION

  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
  Partition 1    Primary            199 MB  1024 KB      Windows 7 boot partition
  Partition 2    Primary            282 GB   200 MB       Windows 7 main partition
  Partition 3    Primary             15 GB   282 GB        Windows 7 recovery partition
  Partition 4    Primary            103 MB   297 GB       HP Tools partition
```The thing is .. I do not want to touch Windows 7 recovery and HP Tools. Since I'm going to format Windows 7 main partition and replace with Ubuntu, I guess I don't need the boot partition either ?

Anyway, the question is .. should I install GRUB on /dev/sda ( whole disk ) or /dev/sda1 ( first partition ) ?

---

### Post by wilee-nilee on 2011-05-14
> **Minimal Hank said:**
> I thought I should try Ubuntu on my new laptop but I'm stuck with where to install GRUB ..

```
DISKPART> LIST PARTITION

  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
  Partition 1    Primary            199 MB  1024 KB      Windows 7 boot partition
  Partition 2    Primary            282 GB   200 MB       Windows 7 main partition
  Partition 3    Primary             15 GB   282 GB        Windows 7 recovery partition
  Partition 4    Primary            103 MB   297 GB       HP Tools partition
```The thing is .. I do not want to touch Windows 7 recovery and HP Tools. **Since I'm going to format Windows 7 main partition and replace with Ubuntu**, I guess I don't need the boot partition either ?

Anyway, the question is .. should I install GRUB on /dev/sda ( whole disk ) or /dev/sda1 ( first partition ) ?

You have 4 primary partitions that is the max on a HD, just info here.

So if you're not replacing W7, which to be honest is hard to tell with the wording, you will have to loose a partition.

Chances are if you want a partitioned dual boot your access to the recovery is unlikely.

No big deal you can clone the C drive , do the backup allowed, if a OEM or home only a one time thing.

Most people remove both of the partitions you don't want to part with, the recovery and the firmware/boot partition=1, but you have to make sure that partition 2 in your mock description can boot on its own easily done with a windows install or recovery disc. 

If you do not understand what I  mean or are unsure don't do it and ask questions.;)

---

### Post by MAFoElffen on 2011-05-14
> **Minimal Hank said:**
> I thought I should try Ubuntu on my new laptop but I'm stuck with where to install GRUB ..

```
DISKPART> LIST PARTITION

  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
  Partition 1    Primary            199 MB  1024 KB      Windows 7 boot partition
  Partition 2    Primary            282 GB   200 MB       Windows 7 main partition
  Partition 3    Primary             15 GB   282 GB        Windows 7 recovery partition
  Partition 4    Primary            103 MB   297 GB       HP Tools partition
```The thing is .. I do not want to touch Windows 7 recovery and HP Tools. Since I'm going to format Windows 7 main partition and replace with Ubuntu, I guess I don't need the boot partition either ?

Anyway, the question is .. should I install GRUB on /dev/sda ( whole disk ) or /dev/sda1 ( first partition ) ?
Answer- " /dev/sda "

Tip- Create a Win7 Recovery Disk and do a backup before you delete Win7... Dell and HP use a few propietary files that check the digital signature of their motherboards (In Windows). so If you ever wanted to reinstall Windows (as a dual boot or such), then your going to need those.

---

### Post by wilee-nilee on 2011-05-14
> **MAFoElffen said:**
> Answer- " /dev/sda "

Tip- Create a Win7 Recovery Disk and do a backup before you delete Win7... Dell and HP use a few propietary files that check the digital signature of their motherboards (In Windows). so If you ever wanted to reinstall Windows (as a dual boot or such), then your going to need those.

If the user replaces W7, and does not know about extended partitions and places a swap=5 partition on there as well the HD will go dynamic. 

That is not a good thing.

---

### Post by MAFoElffen on 2011-05-14
> **wilee-nilee said:**
> If the user replaces W7, and does not know about extended partitions and places a swap=5 partition on there as well the HD will go dynamic. 

That is not a good thing.
I was thinking that "same."  He already has 4 partitions marked as primary and should end up with no more than 4 primaries.  If he "replaced" Windows as he sort-of- said, That would be one... He really wouldn't need the recovery or the tools parturition except as a backup.

The tools partition is not really going to do him much good without having Winodws present on it.  The Revovery Partition wouldn't be needed if he made a Recovery disk and Backed up what is there...

That leaves him with the "main" ntfs, which I figure is data? Other Win Programs?

---

### Post by wilee-nilee on 2011-05-14
> **MAFoElffen said:**
> I was thinking that "same."  He already has 4 partitions marked as primary and should end up with no more than 4 primaries.  If he "replaced" Windows as he sort-of- said, That would be one... He really wouldn't need the recovery or the tools parturition except as a backup.

The tools partition is not really going to do him much good without having Winodws present on it.  The Revovery Partition wouldn't be needed if he made a Recovery disk and Backed up what is there...

That leaves him with the "main" ntfs, which I figure is data? Other Win Programs?

I appreciate your candour, we never really know what the other knows until they tell us.;)

---

