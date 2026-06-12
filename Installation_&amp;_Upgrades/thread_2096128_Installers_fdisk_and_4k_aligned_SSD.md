---
title: "Installers fdisk and 4k aligned SSD"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by finite9 on 2012-12-19
I installed 12.10 (server) on a brand new Corsair 120GB Force GT SSD last night.

After installation, fdisk -l shows:

```
Sector size (logical/physical): 512 bytes / 512 bytes

```

Either the device is lying about it's sector size or the installers partitioner hasn't done a good job.

I have other non-SSD devices that report the 4k just fine:

```
Sector size (logical/physical): 512 bytes / 4096 bytes

```

Questions:

If im seeing this on the physical device /dev/sda, does that mean the device is lying about it's own sector size?

If it is lying, does it really matter what fdisk reports as long as all partitions are aligned properly on even sectors that are multiples of 4k?  I cannot check this at the moment.

---

### Post by darkod on 2012-12-19
The info you posted doesn't refer to 4k alignment.

The 512B/4096B refer to the so called 4K HDDs. The bigger capacity HDDs (like 2TB or 3TB) have to have 4KB in one sector, instead of the 512B per sector that the smaller ones have. Otherwise there is no sufficient space on the plates.

The 4k alignment usually refers to the Start sector of the first partition, and it's usually 2048 (that means 1MiB if you calculate 2048 sectors of 512B each).
The rule is more or less that the first sector has to be divisible by 8. Most commonly used value is 2048.

Sometimes parted gives you better organized and precise results than fdisk. Try listing the disks with parted using sectors as units:
sudo parted -l unit s

---

### Post by finite9 on 2012-12-19
Got very befuddled at your reply... it means I must have totally misunderstood the whole issue, and on every website i've been to to get info on this, i've just been giving myself positive re-arffirmation :(  bummer.

Yes, my SSD is a 4k model, and from what I have read, I have understood that to be synonymous with problems with formatting 4k devices where the issue is sector alignment, in that, if first partition starts at sector 1, then it breaks the internal method of reading/writing in 4k blocks, and performance suffers as a result (because then you're having to read multiple blocks to service the IO request).

I had interprested the issue as: if you format the disk so that partitions begin on multiples of 4k then the disk would internally by reading correctly in 4k blocks and performance would be optimal.

In fact, now when I think about it, I start to feel that you are confusing the issue, because I was on #parted and on #ubuntu-server on Freenode this morning and asked the same questions there, and they seemed to share exactly my world view about this issue.  It would be interesting to read someone elses comment on this.

---

### Post by darkod on 2012-12-19
I don't think I am confusing anything. We are basically saying the same thing, maybe my reply was confusing.

You are right about the 4KiB alignment and that it helps performance. If I'm not mistaken, all it needs is that the first partition starts at a multiple of 4KiB and the partition size is multiple of 4KiB.

So, like I said, if your first partition starts at sector 2048, that means 1MiB which is multiple of 4KiB, so it complies with the alignment requirement. Also, the partitions you are creating are probably in GiBs so they would also be multiples of 4KiB.
That is why the important thing is the start of the first partition, and later all other partitions are aligned too.

If fdisk says /dev/sda1 starts at sector 2048, you are good.

What you posted is the info about the sector size, and that is not exactly the same as aligning, although it is related because we are talking about aligning the hdd and those sector sizes are on the hdd. That info only tells you how many Bytes do the logical and physical sectors have on the HDD.

PS EDIT: For example, you can easily have a HDD which has physical sector of 4KiB misaligned. Create a partition on that HDD that starts at sector 4321 and it will be misaligned. The HDD having 4KiB sectors has nothing to do with 4KiB alignment.

---

### Post by finite9 on 2012-12-20
Yes, Ok, I understand what you are saying now, and it makes sense to me.

By the way, I checked my output from fdisk, and the Ubuntu 12.10 installer _does_ configure the partitions so that the first is on 2048, and all other partitions are also aligned to a 4k boundary, so everything is looking good!

I have other Seagate disks that report 4096B physical sector size, so it looks like the Corsair SSD maybe reporting it wrong for compatibility with XP, which, as I now understand, doesn't make any difference as long as the partitions are aligned properly.

Thanks for taking the time to reply.

---

### Post by marcosestevesbarbosa on 2013-06-16
Ubuntu installer create the begin of partition on the right place? You can try with 13.04  desktop installer?

---

