---
title: "Laptop, Hibernate, Swapfile.....How dumb am I???"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by WTF_Shelley on 2012-12-26
A have a quick question about suspend/resume hibernate from a swapfile.  My laptop a Toshiba p750 with 8gig and a 128g ssd,  when ever i try to set up a multipartition system on the ssd i get the alignment incorrect and speeds / trim gets a bit wonky.

So i decided to use a swap file which i created in the root partition with

```
dd if=/dev/zero of=/swapfile.swap bs=1024 count=9437184
mkswap /swapfile.swap
chown root:root /swapfile.swap
chmod 0600 /swapfile.swap
```

and added this to /etc/fstab

```
/swapfile.swap  swap    swap    defaults        0       0

```
this is where i think i made a couple of mistakes.  Using a bunch of info from random forums and a very dry debian howto from 2010. i ran 

```
filefrag -v /swapfile.swap
Filesystem type is: ef53
File size of /swapfile.swap is 9663676416 (2359296 blocks, blocksize 4096)
 ext logical physical expected length flags
   0       0   569344            2048 
   1    2048   579584   571392   4096 
....
snip
....
  75 2279424  3110912           32768 
  76 2312192  3143680            2048 
  77 2314240  3182592  3145728  32768 
  78 2347008  3215360           12288 eof
/swapfile.swap: 16 extents found
```

to find where the file is located and finally added 

```
resume=/dev/sda1 resume_offset=569344

```
to my kernel line.  Now this all works.

im worried that the hibernate will over run the swapfile and corrupt the filesystem?

---

