---
title: "How to save data"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by Cool Surfer on 2007-06-03
How to protect data like my files and folders from getting erased with a linux/ubuntu reinstall.
I want to keep data on one linux partition and install the os files on another. During the install it I could make ext3 10gb and a swap 3gb partition.

How should I add a 40gb partition, in ext2 or ext3 format?

Thanks

---

### Post by wpshooter on 2007-06-03
Make / for your** root** or **O/S** installation.

Make /home for your personal, etc. non O/S files.

Make /swap for your swap.

Files system types would be root - EXT3, /home - EXT3, swap - SWAP.

Then in the future if you reinstall for some reason just do NOT format /home and any subdirectories under /home.

Good luck.

---

### Post by Cool Surfer on 2007-06-04
So home should be entirely on a different partition?
Right now I had made just 2 partitions - swap , n ext3 for os.

---

### Post by jfinkels on 2007-06-04
> **Cool Surfer said:**
> So home should be entirely on a different partition?
Right now I had made just 2 partitions - swap , n ext3 for os.

Yep, your partitions will look like this (as stated above):
/ - ext3, 5-10 GB
swap - swap, twice the size of your RAM
/home - ext3, the remaining size of your hard drive

---

### Post by Cool Surfer on 2007-06-04
This is cool The help is almost instantaneous. :)

---

### Post by crawall on 2008-01-07
how do i make a partition with name /home

---

