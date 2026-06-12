---
title: "Is this a slow RAID5?"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by Ueland on 2008-02-01
Hi,

I have set up a RAID5 with 6 200GB IDE disks, and are a bit unshure about the speeds. Should i be satesfied with theese speeds? :)

The resync is not to quick, allthrough i have increased min/max speed.

MDstatus:
> Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdk[0] sdg[6] sdf[4] sdn[3] sdm[2] sdl[1]
      976804480 blocks level 5, 64k chunk, algorithm 2 [6/5] [UUUUU_]
      [=======>.............]  recovery = 35.5% (69379456/195360896) finish=122.2min **speed=17169K/sec**

unused devices: <none>



Result of DD from the RAID while resyncing: (WITH ReiserFS)
> 
dd if=/dev/zero of=testing bs=1M count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 24.876 seconds, 43.2 MB/s


Result of DD from the RAID while resyncing: (WITH XFS)
> 
dd if=/dev/zero of=testing bs=1M count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 19.181 seconds, 56.0 MB/s


I also have 8 SATA disks that i will set up after the IDEs, so il also have a look on how the speed is on those afterwards.

---

### Post by kidders on 2008-02-03
Hi there,

I'm afraid there is simply no way to tell. I/O performance is very heavily dependent on hardware, and how it's been configured. From what you've posted, it's not even valid to conclude that XFS is any faster than ReiserFS.

If you're concerned about performance, it's worth checking for daft things (eg filesystem & RAID block sizes that don't align properly), but beyond that, the limitations of your particular combination of hardware determine how fast you can pump data through it. Having said that, the speeds you posted don't *seem* insanely low.

---

### Post by Ueland on 2008-02-03
I did some new testing after the RAID`s was done syncing and i ended on around 200-250MB/s on read, and 70-100MB/s write, so i cant complain about that. :)

---

