---
title: "Can't install Gutsy. Edgy and Feisty were fine."
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by michaeljustman on 2007-10-10
I recently tried installing Gutsy Gibbon Beta on my Panasonic zv6000 laptop. I've run both Edgy Eft and Feisty Fawn on this laptop (never did get compositing working on Feisty).

I'm using the ubuntu-7.10-beta-desktop-i386.iso cd image and I've checked the MD5 to make sure the download was good. I burned it to a cd-rw and booted it.

I have no problems using the LiveCD, but when I try to install Gutsy into an 8GB partition I've already prepared to be EXT3 it freezes up at 5%.

It says that it's trying to prepare the partition or something like that and it stays like that for an hour (didn't watch it any longer.)

The partition is after my windows partition (NTFS) and before my data partition (NTFS). I'm installing home into the / partition because I'm going to just use symbolic links to my personal folders on other drives.

I think it might be that I'm not installing it with a swap partition, but I'm not sure. I was going to set up a swap file in the / partition like I had on Edgy and Feisty. I really don't feel like making a swap partition because I only have 80GB to work with.

Any help (even telling me how to submit a bug report) would be appreciated. Thanks.

---

### Post by Pumalite on 2007-10-10
With less than 10 GB, you are wasting your time and you do need a /swap partition= 2x RAM up to 1 GB

---

### Post by michaeljustman on 2007-10-10
I know that you don't need a separate partition for swap. I've ran linux with a file used as swap forever and never had problems. I just don't see the need in messing with my partition table.

As for needing more than 8GB. I'm pretty sure I don't. I ran Edgy and Feisty before and they never got close to using 8GB. The one partition is only for the programs, configuration files, source, etc. I don't actually store any data on it, so it is definitely sufficient. (See Puppy Linux or DSL for better examples of how small linux really is.)

Anyway. I guess this'll bump this post and someone that knows something might reply.

---

