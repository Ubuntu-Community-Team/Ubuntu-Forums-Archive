---
title: "Is a /swap partition really necessary?"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by RCC2k7 on 2007-02-02
OK, here's what happened. When I decided to install Ubuntu I set aside 40GB of unpartitioned space for it to use. I didn't like the fact that the Ubuntu installer decided to use those 40 GB for the system and to steal 2 extra GB by resizing an NTFS data partition for use as a swap partition.

I didn't do much about it initially, but last night I removed Ubuntu and its swap partition in order to try openSuSE 10.2. OpenSuSE made an even bigger mess with my partitions so I decided to set things straight and revert my system to the state where only 40GB was set aside to try Linux. I managed to install openSuSE within that space, but then decided to come back to Ubuntu. Instead of installing Ubuntu again, I restored an image I had backed, restoring the 40 GB system partition and not the 2 GB swap partition that was stolen without my consent.

Ubuntu boots normally - no error messages were given about the now missing /swap partition. Is it really necesary to have a /swap partition? Can't Linux just swap to a /swap folder on the main partition?

---

### Post by kingmonkey on 2007-02-02
It depends how much RAM you have, type free to see how much RAM is free, if its building up then you might benefit from having /swap.

Yes you can use a swap file as a /swap partition.

---

### Post by RCC2k7 on 2007-02-02
> **kingmonkey said:**
> It depends how much RAM you have, type free to see how much RAM is free, if its building up then you might benefit from having /swap.

Yes you can use a swap file as a /swap partition.

Thanks. I have 2 GB of RAM. This is what Ubuntu reports for it:
```

             total       used       free     shared    buffers     cached
Mem:          2026        500       1525          0         14        233
-/+ buffers/cache:        252       1773
Swap:            0          0          0

```
How do I make the system to use a swap file from a folder on the main partition instead of a /swap partition?

---

### Post by raul_ on 2007-02-02
I have a 150mb file :P it never gets more than 11% use and i have 1gb of RAM. My guess is that you dont need swap at all...if you still want it just create a 100mb swap file

EDIT: Wrong link...i'll post the right one in a minute

[http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/]("http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/")

you can replace "swapfile1" with "swap" or any name you want

---

### Post by Paerez on 2007-02-02
Swap is very important to me since I am a laptop user and I like to hibernate. I guess I could be using a swap file instead.

Historically it is set up as a different partition so that you can have the operating system on one physical drive and the swap on another to improve performance.

---

### Post by glabouni on 2007-02-02
for computer with 1GB RAM or more, swap is seldomly or never used (depends on what you do with your computer.).

it is possible but not recommended to use a swap file over a swap partition, if your system need to swap and the disk is full, system can become very sluggish, halt or crash.

anyways with 2GB you don't really need a swap file, if I were you I would make a 512MB swap partition just for peace of mind.

---

### Post by RCC2k7 on 2007-02-02
Thanks, raul_ That worked!!! =D>

---

