---
title: "tri-boot with DOS, Win98, and ubuntu question"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by tzykid on 2006-11-28
I am working on putting three OS's on a system. I'm going to use DOS, win98, and ubuntu useing the Grub from ubuntu as the boot manager (only OS listed that has a boot manager). I know that duel-booting with Win98 is easy, but I haven't had any experience with DOS/ubuntu on the same system. I haven't found anything on DOS 6.22/ubuntu interaction so was curious if there was anything different I needed to do for DOS to work correctly. I am kinda new to ubuntu, and if there is anything I should be aware of when trying to tri-boot that is different than a duel-boot please any advice would be very appreciated.

---

### Post by lha on 2006-11-28
Making Ubuntu work with DOS and/or Win98 is easy. It is a bit trickier to install DOS and Windows if you want to put them on different partitions. "The Microsoft Way" to dual-boot DOS and Win98 is to install DOS first and Windows on top of it, so they have are on a common partition. (Not good in my opinion, DOS 6.22 doesn't support fat32 and 2GB max. partition size of fat16 is a bit small.) Both DOS and Win98 want to be on the first primary partition, so if you put them on separate partitions, you have to hide Windows's partition when booting DOS and vice versa.

---

